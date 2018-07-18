---
title: コンテナーの高度な例
description: ''
ms.custom: ''
ms.date: 04/18/2018
ms.technology: vs-acquisition
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: e03835db-a616-41e6-b339-92b41d0cfc70
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c941928495dc39dc6b6ecbe9600f39dad969fec2
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2018
ms.locfileid: "31621146"
---
# <a name="advanced-example-for-containers"></a>コンテナーの高度な例

「[Build Tools をコンテナーにインストールする](build-tools-container.md)」のサンプル Dockerfile は常に、最新の microsoft/windowsservercore イメージに基づく [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) イメージと、最新の Visual Studio Build Tools 2017 インストーラーを使用します。 他のユーザーがプルできるようにこのイメージを [Docker レジストリ](https://azure.microsoft.com/services/container-registry)に発行すると、このイメージが多くのシナリオで使用できるようになります。 ただし、実際には、どの基本イメージを使用するか、どのバイナリをダウンロードするか、どのツールのバージョンをインストールするかによって異なることが一般的です。

以下の Dockerfile の例では、microsoft/dotnet-framework イメージの特定バージョンのタグを使用します。 基本イメージに固有のタグを使用することが一般的であり、これによってイメージのビルドまたはリビルドで常に同じ基準を使用することが簡単になります。

> [!NOTE]
> コンテナーのインストーラーの起動に既知の問題がある、microsoft/windowsservercore:10.0.14393.1593 またはそれに基づくイメージに Visual Studio をインストールすることはできません。 詳細については、[既知の問題](build-tools-container-issues.md)に関するページを参照してください。

次の例では、Build Tools 2017 の最新リリースをダウンロードします。 後でコンテナーにインストールできる古いバージョンの Build Tools を利用したい場合は、最初にレイアウトを[作成](create-an-offline-installation-of-visual-studio.md)して[維持](update-a-network-installation-of-visual-studio.md)する必要があります。

## <a name="install-script"></a>インストール スクリプト

インストール エラーが発生したときにログを収集するには、作業ディレクトリに、次のような内容で "Install.cmd" という名前のバッチ スクリプトを作成します。

```shell
@if not defined _echo echo off
setlocal enabledelayedexpansion

call %*
if "%ERRORLEVEL%"=="3010" (
    exit /b 0
) else (
    if not "%ERRORLEVEL%"=="0" (
        set ERR=%ERRORLEVEL%
        call C:\TEMP\collect.exe -zip:C:\vslogs.zip

        exit /b !ERR!
    )
)
```

## <a name="dockerfile"></a>Dockerfile

作業ディレクトリに、次のような内容の "Dockerfile" を作成します。

```dockerfile
# escape=`

# Use a specific tagged image. Tags can be changed, though that is unlikely for most images.
# You could also use the immutable tag @sha256:1a66e2b5f3a5b8b98ac703a8bfd4902ae60d307ed9842978df40dbc04ac86b1b
ARG FROM_IMAGE=microsoft/dotnet-framework:4.7.1-20180410-windowsservercore-1709
FROM ${FROM_IMAGE}

# Copy our Install script.
COPY Install.cmd C:\TEMP\

# Download collect.exe in case of an install failure.
ADD https://aka.ms/vscollect.exe C:\TEMP\collect.exe

# Use the latest release channel. For more control, specify the location of an internal layout.
ARG CHANNEL_URL=https://aka.ms/vs/15/release/channel
ADD ${CHANNEL_URL} C:\TEMP\VisualStudio.chman

# Download and install Build Tools excluding workloads and components with known issues.
ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe
RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
    --installPath C:\BuildTools `
    --channelUri C:\TEMP\VisualStudio.chman `
    --installChannelUri C:\TEMP\VisualStudio.chman `
    --all `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
    --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
    --remove Microsoft.VisualStudio.Component.Windows81SDK

# Start developer command prompt with any other commands specified.
ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

# Default to PowerShell if no other command specified.
CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
```

次のコマンドを実行して、現在の作業ディレクトリでイメージをビルドします。

```shell
docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
```

必要に応じて、`--build-arg` コマンド ライン スイッチを使用し、`FROM_IMAGE` 引数と `CHANNEL_URL` 引数のどちらか一方または両方を渡して、別の基本イメージ、または固定イメージを維持するための内部レイアウトの場所を指定します。

## <a name="diagnosing-install-failures"></a>インストールの失敗の診断

この例では、特定のツールをダウンロードし、ハッシュが一致したことを検証します。 インストール エラーが発生した場合にログをホスト コンピューターにコピーしてエラーを分析できるように、最新の Visual Studio と .NET ログ コレクションもダウンロードします。

```shell
> docker build -t buildtools2017:15.6.27428.2037 -t buildtools2017:latest -m 2GB .
Sending build context to Docker daemon
...
Step 8/10 : RUN C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache ...
 ---> Running in 4b62b4ce3a3c
The command 'cmd /S /C C:\TEMP\Install.cmd C:\TEMP\vs_buildtools.exe ...' returned a non-zero code: 1603

> docker cp 4b62b4ce3a3c:C:\vslogs.zip "%TEMP%\vslogs.zip"
```

最終行の実行が終了したら、コンピューターで "%TEMP%\vslogs.zip" を開くか、[開発者コミュニティ](https://developercommunity.visualstudio.com)の Web サイトで問題を提出します。

## <a name="get-support"></a>サポートを受ける

ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング](troubleshooting-installation-issues.md)」ページをご覧ください。 トラブルシューティングの手順でも解決しない場合は、ライブ チャットでインストールの支援を依頼してください (英語のみ)。 詳細については、[Visual Studio のサポート ページ](https://www.visualstudio.com/vs/support/#talktous)をご覧ください。

他のいくつかのサポート オプションを次に示します。

* Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。
* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関するスレッド](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。 (このオプションでは [GitHub](https://github.com/) アカウントが必要になります)。

## <a name="see-also"></a>関連項目

* [コンテナーにビルド ツールをインストールする](build-tools-container.md)
* [コンテナーの既知の問題](build-tools-container-issues.md)
* [Visual Studio Build Tools 2017 のワークロード ID とコンポーネント ID](workload-component-id-vs-build-tools.md)
