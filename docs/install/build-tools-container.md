---
title: Visual Studio Build Tools をコンテナーにインストールする
titleSuffix: ''
description: Visual Studio Build Tools を Windows コンテナーにインストールして、継続的インテグレーションと継続的デリバリー (CI/CD) のワークフローをサポートする方法を説明します。
ms.date: 04/18/2018
ms.custom: seodec18
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d5c038e2-e70d-411e-950c-8a54917b578a
author: heaths
ms.author: tglee
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e98ff7f21ab7620092f2b535f17c55ab4d584b7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53946634"
---
# <a name="install-build-tools-into-a-container"></a>Build Tools をコンテナーにインストールする

Visual Studio Build Tools を Windows コンテナーにインストールして、継続的インテグレーションと継続的デリバリー (CI/CD) のワークフローをサポートできます。 この記事では、必要な Docker 構成の変更と、コンテナーにインストールできる[ワークロードとコンポーネント](workload-component-id-vs-build-tools.md)について説明します。

[コンテナー](https://www.docker.com/what-container)は一貫性のあるビルド システムをパッケージ化する優れた手段であり、CI/CD サーバー環境でだけでなく、開発環境でも使うことができます。 たとえば、カスタマイズされた環境でビルドされるようにコンテナーにソース コードをマウントしながら、Visual Studio や他のツールを使って引き続きコードを記述することができます。 お使いの CI/CD ワークフローが同じコンテナー イメージを使っている場合、コードのビルドの一貫性を心配する必要はありません。 実行時の一貫性を保つためにコンテナーを使うこともでき、これはオーケストレーション システムで複数のコンテナーを使っているマイクロサービスでは一般的なことですが、この記事ではそれについては説明しません。

ご自分のソース コードのビルドに必要な機能が Visual Studio Build Tools にない場合は、他の Visual Studio 製品に対して同じ手順を使うことができます。 ただし、Windows コンテナーは対話型のユーザー インターフェイスをサポートしていないため、すべてのコマンドを自動化する必要があることに注意してください。

## <a name="overview"></a>概要

[Docker](https://www.docker.com/what-docker) を使って作成したイメージから、ソース コードをビルドするコンテナーを作成できます。 この例の Dockerfile では、最新の Visual Studio Build Tools 2017 と、ソース コードのビルドによく使われる他の便利なプログラムをインストールします。 独自の Dockerfile をさらに変更して、テストの実行やビルド出力の発行などのための他のツールやスクリプトを組み込むことができます。

Docker for Windows を既にインストールしてある場合は、手順 3 に進んでかまいません。

## <a name="step-1-enable-hyper-v"></a>手順 1. Hyper-V を有効にする

Hyper-V は既定では有効になっていません。 現在、Windows 10 では Hyper-V による分離のみがサポートされているので、Docker for Windows を開始するには Hyper-V を有効にする必要があります。

* [Windows 10 で Hyper-V を有効にする](https://docs.microsoft.com/virtualization/hyper-v-on-windows/quick-start/enable-hyper-v)
* [Windows Server 2016 で Hyper-V を有効にする](https://docs.microsoft.com/windows-server/virtualization/hyper-v/get-started/install-the-hyper-v-role-on-windows-server)

> [!NOTE]
> お使いのコンピューターで仮想化を有効にする必要があります。 通常は既定で有効になっていますが、Hyper-V のインストールが失敗する場合は、システムのドキュメントで仮想化を有効にする方法を参照してください。

## <a name="step-2-install-docker-for-windows"></a>手順 2. Docker for Windows をインストールする

Windows 10 を使っている場合は、[Docker Community Edition for Windows](https://docs.docker.com/docker-for-windows/install) をダウンロードしてインストールできます。 Windows Server 2016 を使用している場合は、[Docker Enterprise Edition をインストールする手順](https://docs.docker.com/install/windows/docker-ee)に従ってください。

## <a name="step-3-switch-to-windows-containers"></a>手順 3. Windows コンテナーに切り替える

Windows には Build Tools 2017 のみをインストールでき、そのためには [Windows コンテナー](https://docs.docker.com/docker-for-windows/#getting-started-with-windows-containers)に切り替える必要があります。 Windows 10 の Windows コンテナーは [Hyper-V による分離](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container)のみをサポートしていますが、Windows Server 2016 の Windows コンテナーは Hyper-V による分離とプロセス分離の両方をサポートしています。

## <a name="step-4-expand-maximum-container-disk-size"></a>手順 4. コンテナーのディスクの最大サイズを増やす

Visual Studio Build Tools さらには Visual Studio 全体では、すべてのツールをインストールするために多くのディスク容量が必要です。 この例の Dockerfile ではパッケージ キャッシュを無効にしていますが、それでも必要な容量を確保するためにコンテナー イメージのディスク サイズを増やす必要があります。 現在 Windows では、Docker 構成を変更することによってのみ、ディスク サイズを増やすことができます。

**Windows 10 の場合**:

1. システム トレイの [Docker for Windows アイコンを右クリック](https://docs.docker.com/docker-for-windows/#docker-settings)して、**[設定]** をクリックします。
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

次の Dockerfile の例を新しいファイルとしてディスクに保存します。 ファイル名を単に "Dockerfile" にすると、既定で認識されます。

> [!WARNING]
> この例の Dockerfile では、コンテナーにインストールできない以前の Windows SDK のみを除外します。 以前のリリースはビルド コマンドが失敗する原因になります。

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
   # escape=`

   # Use the latest Windows Server Core image with .NET Framework 4.7.1.
   FROM microsoft/dotnet-framework:4.7.1

   # Restore the default Windows shell for correct batch processing below.
   SHELL ["cmd", "/S", "/C"]

   # Download the Build Tools bootstrapper.
   ADD https://aka.ms/vs/15/release/vs_buildtools.exe C:\TEMP\vs_buildtools.exe

   # Install Build Tools excluding workloads and components with known issues.
   RUN C:\TEMP\vs_buildtools.exe --quiet --wait --norestart --nocache `
       --installPath C:\BuildTools `
       --all `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10240 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.10586 `
       --remove Microsoft.VisualStudio.Component.Windows10SDK.14393 `
       --remove Microsoft.VisualStudio.Component.Windows81SDK `
    || IF "%ERRORLEVEL%"=="3010" EXIT 0

   # Start developer command prompt with any other commands specified.
   ENTRYPOINT C:\BuildTools\Common7\Tools\VsDevCmd.bat &&

   # Default to PowerShell if no other command specified.
   CMD ["powershell.exe", "-NoLogo", "-ExecutionPolicy", "Bypass"]
   ```

   > [!WARNING]
   > microsoft/windowsservercore に直接基づくイメージの場合は、.NET Framework が正しくインストールされない可能性があり、インストール エラーは示されていません。 インストールが完了した後、マネージド コードが実行しない可能性があります。 代わりに、イメージを [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) 以降に基づくようにします。 また、バージョン 4.7.1 以降のタグが付いたイメージでは、既定の `SHELL` として PowerShell を使用する可能性があり、そのために `RUN` および `ENTRYPOINT` 命令が失敗する場合があることに注意してください。
   >
   > Visual Studio 2017 バージョン 15.8 以前 (すべての製品) は、mcr<span></span>.microsoft\.com\/windows\/servercore:1809 以降には適切にインストールされません。 エラーは表示されません。
   >
   > 詳しくは、「[コンテナーの既知の問題](build-tools-container-issues.md)」をご覧ください。

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

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>関連項目

* [コンテナーの高度な例](advanced-build-tools-container.md)
* [コンテナーの既知の問題](build-tools-container-issues.md)
* [Visual Studio Build Tools 2017 のワークロード ID とコンポーネント ID](workload-component-id-vs-build-tools.md)
