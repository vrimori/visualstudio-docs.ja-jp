---
title: "Python 用 Azure クラウド サービス プロジェクト テンプレート | Microsoft Docs"
ms.custom: 
ms.date: 07/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a2ce82ee-8c73-419a-bbd2-4c3513fd394d
caps.latest.revision: "11"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 3a8f7d9a21a65a8e63ee47cb0783b7345b28d632
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="azure-cloud-service-projects-for-python"></a>Python 用 Azure クラウド サービス プロジェクト

Visual Studio は、Python を使用して Azure Cloud Services の作成に使用できるテンプレートを提供しています。

[クラウド サービス](http://go.microsoft.com/fwlink/?LinkId=306052)は、任意の数の *worker ロール*と *Web ロール*から構成され、それぞれが概念的に独立したタスクを実行しますが、規模拡張の必要に応じて仮想マシン間で個別にレプリケートできます。 Web ロールでは、フロントエンド Web アプリケーションのホスティングが提供されます。 Python が接続されている場合、WSGI をサポートする任意の Web フレームワークを使用して、このようなアプリケーションを作成できます ([Web プロジェクト テンプレート](template-web.md)でサポート)。 worker ロールは、ユーザーと直接対話しない長時間実行されるプロセスを意図しています。 通常、これらは `pip install`&nbsp;[`azure`](http://pypi.org/project/azure) でインストールできる[データ](http://go.microsoft.com/fwlink/?LinkId=401571) ライブラリと[アプリ サービス](http://go.microsoft.com/fwlink/?LinkId=401572) ライブラリを利用します。

このトピックでは、Visual Studio 2017 のプロジェクト テンプレートとその他のサポートについて詳しく説明します (以前のバージョンも同様ですが、いくつかの違いがあります)。 Python からの Azure の操作について詳しくは、[Azure Python デベロッパー センター](http://go.microsoft.com/fwlink/?linkid=254360)をご覧ください。

## <a name="create-a-project"></a>プロジェクトを作成する

1. クラウド サービス テンプレートを使用するために必要な [Azure .NET SDK for Visual Studio](https://www.visualstudio.com/vs/azure-tools/) をインストールします。
1. Visual Studio で、**[ファイル] > [新規] > [プロジェクト...]** を選択し、"Azure Python" を検索して **[Azure クラウド サービス]** を一覧から選びます。

    ![Python 用 Azure クラウド プロジェクト テンプレート](media/template-azure-cloud-project.png)

1. 含める 1 つ以上のロールを選びます。 クラウド プロジェクトは、異なる言語で記述されたロールを結合できるため、アプリケーションの各部分を最も適した言語で簡単に記述できます。 このダイアログの完了後に新しいロールをプロジェクトに追加するには、ソリューション エクスプローラーで **[ロール]** を右クリックし、**[追加]** の下で項目の 1 つを選びます。

    ![Azure クラウド プロジェクト テンプレートでのロールの追加](media/template-azure-cloud-service-project-wizard.png)

1. 個々のロール プロジェクトが作成されるときに、Django、Bottle、Flask フレームワークなどの追加の Python パッケージの 1 つを使用するロールを選んだ場合は、これらをインストールするように求めるプロンプトが表示されることがあります。

1. プロジェクトに新しいロールを追加すると、構成手順がいくつか表示されます。 構成の変更は通常必要ありませんが、プロジェクトの将来のカスタマイズに役立つ場合があります。 同時に複数のロールを追加する場合は、最後のロールについての説明のみ開いたままになります。 ただし、他のロールの手順とトラブルシューティングのヒントは、ロールの ルートまたは `bin` フォルダーにあるそれぞれの `readme.mht` ファイルで参照できます。

1. プロジェクトの `bin` フォルダーには、Python のインストール、プロジェクトの [requirements.txt](#dependencies) ファイル、必要な場合に IIS の設定など、リモート仮想マシンの構成に使用する 1 つまたは 2 つの PowerShell スクリプトも含まれています。 デプロイでの必要に応じてこれらのファイルを編集できますが、最も一般的なオプションは他の方法で管理できます (下の「[ロールのデプロイを構成する](#configuring-role-deployment)」をご覧ください)。 これらのファイルが使用可能でない場合はレガシ構成スクリプトが代わりに使用されるため、これらのファイルの削除はお勧めしません。

    ![worker ロールのサポート ファイル](media/template-azure-cloud-service-worker-role-support-files.png)

    これらの構成スクリプトを新しいプロジェクトに追加するには、プロジェクトを右クリックし、**[追加] > [新しい項目...]** を選び、**[Web ロール サポート ファイル]** または **[worker ロール サポート ファイル]** のいずれかを選びます。
   

## <a name="configuring-role-deployment"></a>ロールのデプロイを構成する

ロール プロジェクトの `bin` フォルダー内の PowerShell スクリプトは、そのロールのデプロイを制御し、編集して構成をカスタマイズできます。

- `ConfigureCloudService.ps1` は、通常は従属物をインストールして構成し、Python のバージョンを設定するために Web ロールと worker ロールに使用されます。
- `LaunchWorker.ps1` は worker ロールにのみ使用され、起動の動作の変更、コマンドライン引数の追加、環境変数の追加に使用されます。

どちらのファイルにも、カスタマイズの手順が含まれます。 メインのクラウド サービス プロジェクトの `ServiceDefinition.csdef` ファイルに別のタスクを追加し、`PYTHON` 変数をインストールされている `python.exe` (または同等の) パスに設定することで、独自のバージョンの Python をインストールすることもできます。 `PYTHON` が設定されている場合、Python は NuGet からインストールされません。

追加の構成は、次のように実行できます。

1. プロジェクトのルート ディレクトリ内の `requirements.txt` ファイルを更新することで、`pip` を使用してパッケージをインストールします。 `ConfigureCloudService.ps1` スクリプトによってデプロイ時にこのファイルがインストールされます。
1. `web.config` ファイル (Web ロール) または `ServiceDefinition.csdef` ファイル (worker ロール) の `Runtime` セクションを変更することで、環境変数を設定します。
1. `ServiceDefinitions.csdef` ファイルの `Runtime/EntryPoint` セクションでコマンド ラインを変更して、worker ロールに使用するスクリプトと引数を指定します。
1. `web.config` ファイルを通じて、Web ロールのメイン ハンドラー スクリプトを設定します。

## <a name="testing-role-deployment"></a>ロールのデプロイをテストする

ロールの書き込み中に、クラウド サービス エミュレーターを使用してクラウド プロジェクトをローカルでテストできます。 エミュレーターは Azure SDK Tools に含まれるもので、クラウド サービスが Azure に発行されるときに使用される環境の制限付きバージョンです。

エミュレーターを起動するには、最初に右クリックして **[スタートアップ プロジェクトに設定]** を選択して、クラウド プロジェクトがソリューションのスタートアップ プロジェクトであることを確認します。 次に、**[デバッグ] > [デバッグの開始]** (F5) または **[デバッグ] > [デバッグなしで開始]** (Ctrl+F5) を選択します。

エミュレーターでの制限により、Python コードをデバッグすることはできません。 したがって、ロールを個別に実行し、発行する前に統合テストにエミュレーターを使用してロールをデバッグすることをお勧めします。


## <a name="deploying-a-role"></a>ロールをデプロイする

**発行**ウィザードを開くには、ソリューション エクスプローラーでロール プロジェクトを選び、メイン メニューから **[ビルド] > [発行]** を選択するか、プロジェクトを右クリックして **[発行]** を選択します。

発行プロセスには 2 つのフェーズが含まれます。 まず、Visual Studio で、クラウド サービスのすべてのロールを含む 1 つのパッケージを作成します。 このパッケージは Azure にデプロイされるもので、ロールごとに 1 台以上の仮想マシンを初期化し、ソースをデプロイします。

各仮想マシンがアクティブになると、`ConfigureCloudService.ps1` スクリプトを実行し、すべての従属物をインストールします。 既定では、このスクリプトは Python の最新バージョンを [NuGet](https://www.nuget.org/packages?q=Tags%3A%22python%22+Authors%3A%22Python+Software+Foundation%22) からインストールし、`requirements.txt` ファイルで指定されたパッケージをインストールします。 

最後に、worker ロールは Python スクリプトの実行を開始する `LaunchWorker.ps1` を実行します。Web ロールは IIS を初期化し、Web 要求の処理を開始します。


## <a name="dependencies"></a>依存関係

クラウド サービスでは、`ConfigureCloudService.ps1` スクリプトは `pip` を使用して Python の従属物のセットをインストールします。 依存関係は、`requirements.txt` という名前のファイルで指定する必要があります (`ConfigureCloudService.ps1` を変更することでカスタマイズできます)。 ファイルは初期化の一部として `pip install -r requirements.txt` で実行されます。

クラウド サービス インスタンスには C コンパイラが含まれていないため、C の拡張子を持つすべてのライブラリはコンパイル済みのバイナリを提供する必要があります。

pip とその従属物に加えて `requirements.txt` 内のパッケージが自動的にダウンロードされ、課金対象の帯域幅の使用としてカウントされる可能性があります。 `requirements.txt` ファイルの管理について詳しくは、「[必要なパッケージの管理](python-environments.md#managing-required-packages)」をご覧ください。

## <a name="troubleshooting"></a>トラブルシューティング

デプロイ後に Web または worker ロールが正常に動作しない場合は、以下を確認します。

- Python プロジェクトの bin\ フォルダーに (少なくとも) 以下が含まれること。
    - `ConfigureCloudService.ps1`
    - `LaunchWorker.ps1` (worker ロールの場合)
    - `ps.cmd`

- Python プロジェクトに、すべての従属物 (またはホイール ファイルのコレクション) を一覧する `requirements.txt` ファイルが含まれること。
- クラウド サービスでリモート デスクトップを有効にし、ログ ファイルを調査します。
- `ConfigureCloudService.ps1` と `LaunchWorker.ps1` のログがリモート マシン上の `C:\Resources\Directory\%RoleId%.DiagnosticStore\LogFiles` フォルダーに格納されていること。
- Web ロールが `web.config` に構成されているパス (`WSGI_LOG` appSetting のパス) に追加のログを書き込めること。 ほとんどの標準的な IIS または FastCGI ロギングも動作すること。
- 現在、`LaunchWorker.ps1.log` ファイルは Python の worker ロールによって表示される出力またはエラーを表示する唯一の方法です。