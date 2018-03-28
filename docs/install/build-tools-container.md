---
title: Build Tools をコンテナーにインストールする | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: heaths
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 95b60369350ad099e53b143ff85adbcef250b8b9
ms.sourcegitcommit: fb1fede41d8c5e459dd222755b0497b9d361bc51
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="install-build-tools-into-a-container"></a>Build Tools をコンテナーにインストールする

Visual Studio Build Tools を Windows コンテナーにインストールして、継続的インテグレーションと継続的配信 (CI/CD) のワークフローをサポートできます。 この記事では、必要な Docker 構成の変更と、コンテナーにインストールできる[ワークロードとコンポーネント](workload-component-id-vs-build-tools.md)について説明します。

[コンテナー](https://www.docker.com/what-container)は一貫性のあるビルド システムをパッケージ化する優れた手段であり、CI/CD サーバー環境でだけでなく、開発環境でも使うことができます。 たとえば、カスタマイズされた環境でビルドされるようにコンテナーにソース コードをマウントしながら、Visual Studio や他のツールを使って引き続きコードを記述することができます。 お使いの CI/CD ワークフローが同じコンテナー イメージを使っている場合、コードのビルドの一貫性を心配する必要はありません。 実行時の一貫性を保つためにコンテナーを使うこともでき、これはオーケストレーション システムで複数のコンテナーを使っているマイクロサービスでは一般的なことですが、この記事ではそれについては説明しません。

ご自分のソース コードのビルドに必要な機能が Visual Studio Build Tools にない場合は、他の Visual Studio 製品に対して同じ手順を使うことができます。 ただし、Windows コンテナーは対話型のユーザー インターフェイスをサポートしていないため、すべてのコマンドを自動化する必要があることに注意してください。

## <a name="overview"></a>概要

[Docker](https://www.docker.com/what-docker) を使って作成したイメージから、ソース コードをビルドするコンテナーを作成できます。 この例の Dockerfile では、最新の Visual Studio Build Tools 2017 と、ソース コードのビルドによく使われる他の便利なプログラムをインストールします。 独自の Dockerfile をさらに変更して、テストの実行やビルド出力の発行などのための他のツールやスクリプトを組み込むことができます。

Docker for Windows を既にインストールしてある場合は、手順 3 に進んでかまいません。

## <a name="step-1-enable-hyper-v"></a>手順 1. Hyper-V を無効にする

Hyper-V は既定では有効になっていません。 現在、Windows 10 では Hyper-V による分離のみがサポートされているので、Docker for Windows を開始するには Hyper-V を有効にする必要があります。

* [Windows 10 で Hyper-V を有効にする](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)
* [Windows Server 2016 で Hyper-V を有効にする](https://docs.microsoft.com/windows-server/virtualization/hyper-v/get-started/install-the-hyper-v-role-on-windows-server)

> [!NOTE]
> お使いのコンピューターで仮想化を有効にする必要があります。 通常は既定で有効になっていますが、Hyper-V のインストールが失敗する場合は、システムのドキュメントで仮想化を有効にする方法を参照してください。

## <a name="step-2-install-docker-for-windows"></a>手順 2. Docker for Windows をインストールする

Windows 10 を使っている場合は、[Docker Community Edition for Windows](https://www.docker.com/docker-windows) をダウンロードしてインストールできます。 PowerShell を使い、Desired State Configuration (DSC) または簡単な単一インストール用の[パッケージ プロバイダー](https://docs.microsoft.com/virtualization/windowscontainers/deploy-containers/deploy-containers-on-server)を使って、[Docker Enterprise Edition for Windows Server 2016 をインストール](https://docs.docker.com/engine/installation/windows/docker-ee)できます。

## <a name="step-3-switch-to-windows-containers"></a>手順 3. Windows コンテナーに切り替える

Windows には Build Tools 2017 のみをインストールでき、そのためには [Windows コンテナー](https://docs.docker.com/docker-for-windows/#getting-started-with-windows-containers)に切り替える必要があります。 Windows 10 の Windows コンテナーは [Hyper-V による分離](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container)のみをサポートしていますが、Windows Server 2016 の Windows コンテナーは Hyper-V による分離とプロセス分離の両方をサポートしています。

## <a name="step-4-expand-maximum-container-disk-size"></a>手順 4. コンテナーのディスクの最大サイズを増やす

Visual Studio Build Tools さらには Visual Studio 全体では、すべてのツールをインストールするために多くのディスク容量が必要です。 この例の Dockerfile ではパッケージ キャッシュを無効にしていますが、それでも必要な容量を確保するためにコンテナー イメージのディスク サイズを増やす必要があります。 現在 Windows では、Docker 構成を変更することによってのみ、ディスク サイズを増やすことができます。

**Windows 10 の場合**:

1. システム トレイの [Docker for Windows アイコンを右クリック](https://docs.docker.com/docker-for-windows/#docker-settings)して、**[設定...]** をクリックします。
2. [[Daemon]\(デーモン\) セクションをクリック](https://docs.docker.com/docker-for-windows/#docker-daemon)します。
3. [**[Basic]\(基本\)** ボタンを **[Advanced]\(詳細\)** に切り替え](https://docs.docker.com/docker-for-windows/#edit-the-daemon-configuration-file)ます。
4. 次の JSON 配列プロパティを追加して、ディスク容量を 120 GB に増やします(Build Tools の拡大を見込んで十分に余裕がある量)。

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   このプロパティは、既にあるプロパティに追加されます。 たとえば、既定のデーモン構成ファイルにこれらの変更を適用すると次のようになります。

   ```json
   {
     "registry-mirrors": [],
     "insecure-registries": [],
     "debug": true,
     "experimental": true,
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

5. **[適用]** をクリックします。

**Windows Server 2016 の場合**:

1. "docker" サービスを停止します。

   ```shell
   sc.exe stop docker
   ```

2. 管理者特権でのコマンド プロンプトで、"%ProgramData%\Docker\config\daemon.json" (または `dockerd --config-file` に対して指定したファイル) を編集します。
3. 次の JSON 配列プロパティを追加して、ディスク容量を 120 GB に増やします(Build Tools の拡大を見込んで十分に余裕がある量)。

   ```json
   {
     "storage-opts": [
       "size=120GB"
     ]
   }
   ```

   このプロパティは、既にあるプロパティに追加されます。
4. ファイルを保存して閉じます。
5. "docker" サービスを開始します。

   ```shell
   sc.exe start docker
   ```

## <a name="step-5-create-and-build-the-dockerfile"></a>手順 5. Dockerfile を作成してビルドする

次の Dockerfile の例を新しいファイルとしてディスクに保存する必要があります。 ファイル名を単に "Dockerfile" にすると、既定で認識されます。

> [!NOTE]
> この例の Dockerfile では、コンテナーにインストールできない古い Windows SDK のみを除外します。 古いリリースはビルド コマンドが失敗する原因になります。

1. コマンド プロンプトを開きます。
2. 新しいディレクトリを作成します (推奨)。

   ```shell
   mkdir C:\BuildTools
   ```

3. この新しいディレクトリに移動します。

   ```shell
   cd C:\BuildTools
   ```

3. 次の内容を C:\BuildTools\Dockerfile に保存します。

   ```dockerfile
   # Use the latest Windows Server Core image.
   FROM microsoft/windowsservercore

   # Download useful tools to C:\Bin.
   ADD https://dist.nuget.org/win-x86-commandline/v4.1.0/nuget.exe C:\\Bin\\nuget.exe

   # Download the Build Tools bootstrapper outside of the PATH.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\\TEMP\\vs_buildtools.exe

   # Add C:\Bin to PATH and install Build Tools excluding workloads and components with known issues.
   RUN setx /m PATH "%PATH%;C:\Bin" \
    && C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache --installPath C:\BuildTools --all \
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 \
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 \
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 \
       --remove Microsoft.VisualStudio.Component.Windows81SDK \
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

4. そのディレクトリで次のコマンドを実行します。

   ```shell
   docker build -t buildtools2017:latest -m 2GB .
   ```

   このコマンドは、2 GB のメモリを使って現在のディレクトリに Dockerfile をビルドします。 ワークロードを何かインストールするときは、既定の 1 GB では不十分です。ただし、ビルドの要件によっては、1 GB のメモリだけでもビルドできる場合があります。

   最後のイメージには "buildtools2017:latest" というタグが付きます。"latest" タグはタグが指定されていない場合の既定値なので、コンテナー内では "buildtools2017" として簡単に実行できます。 さらに[高度なシナリオ](advanced-build-tools-container.md)で特定のバージョンの Visual Studio Build Tools 2017 を使いたい場合は、"latest" 意外にも特定の Visual Studio ビルド番号でコンテナーにタグを付けて、コンテナーが特定のバージョンを一貫して使用できるようにします。

## <a name="step-6-using-the-built-image"></a>手順 6. ビルドされたイメージを使う

イメージができたので、それをコンテナーで実行して対話型と自動の両方のビルドを行うことができます。 この例では開発者コマンド プロンプトを使うので、PATH および他の環境変数は既に構成されています。

1. コマンド プロンプトを開きます。
2. コンテナーを実行し、すべての開発者環境変数が設定された状態で PowerShell 環境を開始します。

   ```shell
   docker run -it buildtools2017
   ```

このイメージを CI/CD ワークフローで使うには、独自の [Azure Container Registry](https://azure.microsoft.com/services/container-registry) または他の内部 [Docker レジストリ](https://docs.docker.com/registry/deploying)に発行して、サーバーがそれを取得するだけでよいようにします。

## <a name="get-support"></a>サポートを受ける
ときには、問題が発生してしまうことがあります。 Visual Studio のインストールが失敗した場合は、「[Troubleshooting Visual Studio 2017 installation and upgrade issues (Visual Studio 2017 のインストールとアップグレードの問題のトラブルシューティング)](troubleshooting-installation-issues.md)」ページをご覧ください。 トラブルシューティングの手順でも解決しない場合は、ライブ チャットでインストールの支援を依頼してください (英語のみ)。 詳細については、[Visual Studio のサポート ページ](https://www.visualstudio.com/vs/support/#talktous)をご覧ください。

他のいくつかのサポート オプションを次に示します。
* Visual Studio インストーラーおよび Visual Studio IDE の両方に表示される [[問題の報告]](../ide/how-to-report-a-problem-with-visual-studio-2017.md) ツールから、製品の問題を Microsoft に報告できます。
* [UserVoice](https://visualstudio.uservoice.com/forums/121579) で、製品に関する提案を投稿できます。
* [Visual Studio 開発者コミュニティ](https://developercommunity.visualstudio.com/)で製品の問題を追跡したり、質問したり、回答を検索したりできます。
* [Gitter コミュニティの Visual Studio に関する掲示板](https://gitter.im/Microsoft/VisualStudio)で、Microsoft や他の Visual Studio 開発者と情報を交換することもできます。  (このオプションでは [GitHub](https://github.com/) アカウントが必要になります)。

## <a name="see-also"></a>関連項目

* [コンテナーの高度な例](advanced-build-tools-container.md)
* [コンテナーの既知の問題](build-tools-container-issues.md)
* [Visual Studio Build Tools 2017 のワークロード ID とコンポーネント ID](workload-component-id-vs-build-tools.md)
