---
title: Windows PowerShell スクリプトを使用して、開発環境およびテスト環境に発行する |Microsoft Docs
description: Visual Studio から Windows PowerShell スクリプトを使用して、開発に発行し、環境をテストする方法について説明します。
author: ghogen
manager: douge
assetId: 5fff1301-5469-4d97-be88-c85c30f837c1
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 9d0142c52fbe40256fc0ab6ec0d5d9fdade243b7
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002719"
---
# <a name="using-windows-powershell-scripts-to-publish-to-dev-and-test-environments"></a>Windows PowerShell スクリプトを使用した開発およびテスト環境への発行

Visual Studio で web アプリケーションを作成するときに、Azure App Service または仮想マシンで Web アプリとして Azure に web サイトの発行を自動化する後で使用できる Windows PowerShell スクリプトを生成できます。 編集し、要件に合わせて Visual Studio エディターでの Windows PowerShell スクリプトを拡張または既存のビルド、テスト、および発行スクリプトとスクリプトを統合できます。

これらのスクリプトを使用して、一時的な使用、サイトのカスタマイズされたバージョン (開発/テスト環境とも呼ばれます) をプロビジョニングできます。 たとえば、Azure の仮想マシンまたはテスト スイートの実行、バグの再現、バグ修正、試用版に提案された変更をテストまたはデモ/プレゼンテーション向けのカスタム環境を設定するための web サイトのステージング スロットには、web サイトの特定のバージョンを設定することがあります。 プロジェクトを発行するスクリプトを作成した後、必要に応じて、スクリプトを再実行して、同一の環境を再作成またはテスト用のカスタム環境を作成する web アプリケーションのビルドでスクリプトを実行できます。

## <a name="prerequisites"></a>必須コンポーネント

* Azure SDK 2.3 以降。 参照してください[Visual Studio のダウンロード](http://go.microsoft.com/fwlink/?LinkID=624384)します。 (Azure SDK を web プロジェクト用のスクリプトを生成する必要はありません。 この機能は web プロジェクト、web ロールではなくクラウド サービスです。)
* Azure PowerShell 0.7.4 以降。 参照してください[をインストールして、Azure PowerShell を構成する方法](/powershell/azure/overview)します。
* [Windows PowerShell 3.0](http://go.microsoft.com/?linkid=9811175)またはそれ以降。

## <a name="additional-tools"></a>その他のツール

その他のツールと Azure 向け開発用 Visual Studio で PowerShell を使用するためのリソースは使用できます。 参照してください[PowerShell Tools for Visual Studio](http://go.microsoft.com/fwlink/?LinkId=404012)します。

## <a name="generating-the-publish-scripts"></a>発行スクリプトの生成

次で新しいプロジェクトを作成するときに、web サイトをホストする仮想マシン用の公開スクリプトを生成する[手順](/azure/virtual-machines/windows/classic/web-app-visual-studio.md?toc=%2fazure%2fvirtual-machines%2fwindows%2fclassic%2ftoc.json)します。 できます[生成 Azure App Service で web アプリ用のスクリプトを発行](/azure/app-service/scripts/app-service-powershell-deploy-github)します。

## <a name="scripts-that-visual-studio-generates"></a>Visual Studio によって生成されるスクリプト

Visual Studio というソリューション レベルのフォルダーが生成されます**PublishScripts** 2 つの Windows PowerShell ファイル、仮想マシンや web サイトで使用できる関数を含むモジュールの公開スクリプトを含む、スクリプトです。 Visual Studio には、デプロイするプロジェクトの詳細を指定する JSON 形式でのファイルも生成されます。

### <a name="windows-powershell-publish-script"></a>Windows PowerShell スクリプトを発行します。

公開スクリプトには、web サイトまたは仮想マシンに展開するための特定の発行手順が含まれています。 Visual Studio には、Windows PowerShell 開発の構文の色分けが用意されています。 ヘルプ、関数が使用して、変化する要件に合わせてスクリプト内の関数を自由に編集することができます。

### <a name="windows-powershell-module"></a>Windows PowerShell モジュール

Visual Studio によって生成される Windows PowerShell モジュールには、公開スクリプトで使用される関数が含まれています。 これらの Azure PowerShell 関数を変更する意図されていません。 参照してください[をインストールして、Azure PowerShell を構成する方法](/powershell/azure/overview)します。

### <a name="json-configuration-file"></a>JSON 構成ファイル

JSON ファイルが作成、**構成**フォルダーを Azure にデプロイするリソースを正確に指定する構成データが含まれています。 Visual Studio によって生成されるファイルの名前は、プロジェクトの名前-WAWS-dev.json 仮想マシンを作成する場合、web サイト、またはプロジェクト名-vm-dev.json を作成した場合です。 Web サイトを作成するときに生成される JSON 構成ファイルの例を次に示します。 ほとんどの値は、説明されています。 Web サイトの名前は、ので、プロジェクト名と一致しない可能性があります、Azure によって生成されます。

```json
{
    "environmentSettings": {
        "webSite": {
            "name": "WebApplication26632",
            "location": "West US"
        },
        "databases": [{
            "connectionStringName": "DefaultConnection",
            "databaseName": "WebApplication26632_db",
            "serverName": "YourDatabaseServerName",
            "user": "sqluser2",
            "password": "",
            "edition": "",
            "size": "",
            "collation": "",
            "location": "West US"
        }]
    }
}
```

仮想マシンを作成するときに、JSON 構成ファイルは、次のように検索します。 クラウド サービスは、仮想マシンのコンテナーとして作成されます。 仮想マシンには、通常のエンドポイントの HTTP および HTTPS 経由で web アクセスと Web Deploy、ローカル コンピューター、リモート デスクトップ、Windows PowerShell から web サイトに発行するエンドポイントが含まれています。

```json
{
    "environmentSettings": {
        "cloudService": {
            "name": "myusernamevm1",
            "affinityGroup": "",
            "location": "West US",
            "virtualNetwork": "",
            "subnet": "",
            "availabilitySet": "",
            "virtualMachine": {
                "name": "myusernamevm1",
                "vhdImage": "a699494373c04fc0bc8f2bb1389d6106__Win2K8R2SP1-Datacenter-201403.01-en.us-127GB.vhd",
                "size": "Small",
                "user": "vmuser1",
                "password": "",
                "enableWebDeployExtension": true,
                "endpoints": [{
                        "name": "Http",
                        "protocol": "TCP",
                        "publicPort": "80",
                        "privatePort": "80"
                    },
                    {
                        "name": "Https",
                        "protocol": "TCP",
                        "publicPort": "443",
                        "privatePort": "443"
                    },
                    {
                        "name": "WebDeploy",
                        "protocol": "TCP",
                        "publicPort": "8172",
                        "privatePort": "8172"
                    },
                    {
                        "name": "Remote Desktop",
                        "protocol": "TCP",
                        "publicPort": "3389",
                        "privatePort": "3389"
                    },
                    {
                        "name": "Powershell",
                        "protocol": "TCP",
                        "publicPort": "5986",
                        "privatePort": "5986"
                    }
                ]
            }
        },
        "databases": [{
            "connectionStringName": "",
            "databaseName": "",
            "serverName": "",
            "user": "",
            "password": ""
        }],
        "webDeployParameters": {
            "iisWebApplicationName": "Default Web Site"
        }
    }
}
```

発行スクリプトを実行するときの動作を変更する JSON 構成を編集することができます。 `cloudService`と`virtualMachine`セクションは、必須です。 ただし削除することができます、`databases`セクション必要としない場合。 Visual Studio によって生成される既定の構成ファイルで空プロパティは省略可能です。既定の構成ファイルに値を持つこれらのプロパティが必要です。

を Azure での 1 つの実稼働サイトではなく複数のデプロイ環境 (スロットとも呼ばれます) を持つ web サイトがある場合は、JSON 構成ファイルで web サイトのスロット名を含めることができます。 という web サイトがある場合など**mysite**という名前のスロット**テスト**、URI は`mysite-test.cloudapp.net`が、構成ファイルで使用する正しい名前は mysite (test)。 行える場合、この web サイトとスロットは、サブスクリプションに既に存在します。 存在しない場合は、web サイトを作成、スクリプトを実行すると、スロットを指定せずでスロットを作成し、 [Azure portal](https://portal.azure.com/)、変更された web サイトの名前で、スクリプトを実行します。 Web アプリのデプロイ スロットの詳細については、次を参照してください。[を設定すると、Azure App Service で web アプリのステージング環境](/azure/app-service/web-sites-staged-publishing)します。

## <a name="how-to-run-the-publish-scripts"></a>発行スクリプトを実行する方法

決しての前に Windows PowerShell スクリプトを実行した場合は、スクリプトの実行を有効にする実行ポリシーをまず設定する必要があります。 ポリシーは、ユーザーがスクリプトを実行するマルウェアやウイルスに対して脆弱である場合は、Windows PowerShell スクリプトを実行できないようにするセキュリティ機能です。

### <a name="run-the-script"></a>スクリプトを実行します

1. プロジェクトの Web 配置パッケージを作成します。 Web Deploy パッケージは、web サイトや仮想マシンにコピーするファイルを含む圧縮済みアーカイブ (.zip ファイル) です。 Visual Studio で Web Deploy パッケージを作成するには、web アプリケーション。

   ![Web 作成パッケージの展開](./media/vs-azure-tools-publishing-using-powershell-scripts/IC767885.png)

   詳細については、次を参照してください。[方法: Visual Studio で Web 配置パッケージを作成する](https://msdn.microsoft.com/library/dd465323.aspx)します。 Web 配置パッケージの作成を自動化することも[のカスタマイズと発行スクリプトの拡張](#customizing-and-extending-publish-scripts)します。

1. **ソリューション エクスプ ローラー**スクリプトでは、コンテキスト メニューを開き、選択し、 **PowerShell ISE で開く**します。
1. このコンピューターに Windows PowerShell スクリプトを実行して、最初に場合、管理者特権でコマンド プロンプト ウィンドウを開くし、次のコマンドを入力します。

    ```powershell
    Set-ExecutionPolicy RemoteSigned
    ```

1. 次のコマンドを使用して Azure にサインインします。

    ```powershell
    Add-AzureAccount
    ```

    入力を求められたら、ユーザー名とパスワードを指定します。

    スクリプトを自動化する Azure の資格情報を提供するためには、このメソッドが機能しないに注意してください。 代わりに、使用する必要があります、`.publishsettings`資格情報を提供するファイル。 1 回のみ、コマンドを使用する**Get-azurepublishsettingsfile**を Azure からファイルをダウンロードし、それ以降を使用して、 **Import-azurepublishsettingsfile**ファイルをインポートします。 詳細については、次を参照してください。[をインストールして、Azure PowerShell を構成する方法](/powershell/azure/overview)します。

1. (省略可能)データベース、および、web アプリケーションを発行せず web サイトを使用して、仮想マシンなどの Azure リソースを作成する場合、 **Publish-webapplication.ps1**コマンドと、 **-構成**引数は、JSON 構成ファイルに設定します。 このコマンドラインは、JSON 構成ファイルを使用して、作成するリソースを決定します。 その他のコマンドライン引数の既定の設定を使用しているため、リソースが作成されますが、web アプリケーションは発行されません。 – Verbose オプションは、何が起こっているかについて詳細を提供します。

    ```powershell
    Publish-WebApplication.ps1 -Verbose –Configuration C:\Path\WebProject-WAWS-dev.json
    ```

1. 使用して、 **Publish-webapplication.ps1**コマンドのいずれかのスクリプトを起動し、web アプリケーションを発行するには、次の例で示すようにします。 サブスクリプション名など、他の引数のいずれかの既定の設定をオーバーライドし、パッケージの名前、仮想マシンの資格情報、またはデータベース サーバーの資格情報を発行する必要がある場合は、これらのパラメーターを指定できます。 使用して、 **– Verbose**公開プロセスの進行状況に関する詳細を表示するオプション。

    ```powershell
    Publish-WebApplication.ps1 –Configuration C:\Path\WebProject-WAWS-dev-json `
    –SubscriptionName Contoso `
    -WebDeployPackage C:\Documents\Azure\ADWebApp.zip `
    -DatabaseServerPassword @{Name="dbServerName";Password="adminPassword"} `
    -Verbose
    ```

    仮想マシンを作成する場合、コマンドは、次のようになります。 この例では、複数のデータベースの資格情報を指定する方法も示します。 これらのスクリプトを作成する仮想マシンの場合、SSL 証明書は信頼されたルート機関からされませんが。 そのため、使用する必要があります、 **– AllowUntrusted**オプション。

    ```powershell
    Publish-WebApplication.ps1 `
    -Configuration C:\Path\ADVM-VM-test.json `
    -SubscriptionName Contoso `
    -WebDeployPackage C:\Path\ADVM.zip `
    -AllowUntrusted `
    -VMPassword @{name = "vmUserName"; password = "YourPasswordHere"} `
    -DatabaseServerPassword @{Name="server1";Password="adminPassword1"}, @{Name="server2";Password="adminPassword2"} `
    -Verbose
    ```

    スクリプトは、データベースを作成できますが、データベース サーバーは作成されません。 データベース サーバーを作成する場合は、使用、 **New-azuresqldatabaseserver** Azure モジュールの関数。

## <a name="customizing-and-extending-the-publish-scripts"></a>カスタマイズと発行スクリプトの拡張

発行スクリプトと JSON 構成ファイルをカスタマイズすることができます。 Windows PowerShell モジュール内の関数**AzureWebAppPublishModule.psm1**変更するものではありません。 別のデータベースを指定するか、仮想マシンのプロパティの一部を変更するだけの場合は、JSON 構成ファイルを編集します。 内の関数スタブを実装することができますを構築し、プロジェクトのテストを自動化するスクリプトの機能を拡張する場合は、 **Publish-webapplication.ps1**します。

プロジェクトのビルドを自動化するには、MSBuild を呼び出すコードを追加`New-WebDeployPackage`このコード例で示すようにします。 MSBuild コマンドへのパスは、インストールした Visual Studio のバージョンによって異なります。 正しいパスを取得するには、関数を使用することができます**Get-msbuildcmd**この例のようにします。

### <a name="to-automate-building-your-project"></a>プロジェクトのビルドを自動化するには

1. 追加、`$ProjectFile`グローバル パラメーター セクション内のパラメーター。

    ```powershell
    [Parameter(Mandatory = $false)]
    [ValidateScript({Test-Path $_ -PathType Leaf})]
    [String]
    $ProjectFile,
    ```

1. 関数をコピー`Get-MSBuildCmd`スクリプト ファイルにします。

    ```powershell
    function Get-MSBuildCmd
    {
            process
    {

                $path =  Get-ChildItem "HKLM:\SOFTWARE\Microsoft\MSBuild\ToolsVersions\" |
                                    Sort-Object {[double]$_.PSChildName} -Descending |
                                    Select-Object -First 1 |
                                    Get-ItemProperty -Name MSBuildToolsPath |
                                    Select -ExpandProperty MSBuildToolsPath

                $path = (Join-Path -Path $path -ChildPath 'msbuild.exe')

            return Get-Item $path
        }
    }
    ```

1. 置換`New-WebDeployPackage`で、次のコードおよび構築している行内のプレース ホルダー`$msbuildCmd`します。 このコードでは、Visual Studio 2015 用です。 Visual Studio 2017 を使用している場合は、変更、 **VisualStudioVersion**プロパティを`15.0`(`12.0` for Visual Studio 2013)。

    ```powershell
    function New-WebDeployPackage
    {
        #Write a function to build and package your web application
    ```

    Web アプリケーションを構築するには、MsBuild.exe を使用します。 ヘルプについては、MSBuild コマンド ライン リファレンスを参照してください。 [http://go.microsoft.com/fwlink/?LinkId=391339](http://go.microsoft.com/fwlink/?LinkId=391339)

    ```powershell
    Write-VerboseWithTime 'Build-WebDeployPackage: Start'

    $msbuildCmd = '"{0}" "{1}" /T:Rebuild;Package /P:VisualStudioVersion=14.0 /p:OutputPath="{2}\MSBuildOutputPath" /flp:logfile=msbuild.log,v=d' -f (Get-MSBuildCmd), $ProjectFile, $scriptDirectory

    Write-VerboseWithTime ('Build-WebDeployPackage: ' + $msbuildCmd)
    ```

### <a name="start-execution-of-the-build-command"></a>ビルド コマンドの実行を開始します。

```powershell
$job = Start-Process cmd.exe -ArgumentList('/C "' + $msbuildCmd + '"') -WindowStyle Normal -Wait -PassThru

if ($job.ExitCode -ne 0) {
    throw('MsBuild exited with an error. ExitCode:' + $job.ExitCode)
}

#Obtain the project name
$projectName = (Get-Item $ProjectFile).BaseName

#Construct the path to web deploy zip package
$DeployPackageDir =  '.\MSBuildOutputPath\_PublishedWebsites\{0}_Package\{0}.zip' -f $projectName

#Get the full path for the web deploy zip package. This is required for MSDeploy to work
$WebDeployPackage = Resolve-Path –LiteralPath $DeployPackageDir

Write-VerboseWithTime 'Build-WebDeployPackage: End'

return $WebDeployPackage
}
```

1. 呼び出す、`New-WebDeployPackage`この行の前に関数: `$Config = Read-ConfigFile $Configuration` web apps 用または`$Config = Read-ConfigFile $Configuration -HasWebDeployPackage:([Bool]$WebDeployPackage)`の仮想マシン。

    ```powershell
    if($ProjectFile)
    {
    $WebDeployPackage = New-WebDeployPackage
    }
    ```

1. カスタマイズしたスクリプトを渡すを使用してコマンドラインから起動、`$Project`次の例のように、引数。

    ```powershell
    .\Publish-WebApplicationVM.ps1 -Configuration .\Configurations\WebApplication5-VM-dev.json `
    -ProjectFile ..\WebApplication5\WebApplication5.csproj `
    -VMPassword @{Name="VMUser";Password="Test.123"} `
    -AllowUntrusted `
    -Verbose
    ```

    アプリケーションのテストを自動化する追加のコードを`Test-WebApplication`します。 内の行のコメントを必ず**Publish-webapplication.ps1**これらの関数と呼ばれます。 実装を指定しなかった場合、Visual Studio でプロジェクトを手動でビルドし、Azure に発行する発行スクリプトを実行できます。

## <a name="publishing-function-summary"></a>発行関数の概要
Windows PowerShell コマンド プロンプトで使用できる関数のヘルプを表示するコマンドを使用して、`Get-Help function-name`します。 ヘルプには、パラメーターのヘルプと例が含まれています。 同じヘルプ テキストは、スクリプト ソース ファイルも**AzureWebAppPublishModule.psm1**と**Publish-webapplication.ps1**します。 スクリプトとヘルプは、Visual Studio の言語でローカライズされます。

**AzureWebAppPublishModule**

| 関数名 | 説明 |
| --- | --- |
| 追加 AzureSQLDatabase |新しい Azure SQL database を作成します。 |
| 追加 AzureSQLDatabases |Visual Studio によって生成される JSON 構成ファイル内の値から Azure SQL データベースを作成します。 |
| 追加 AzureVM |Azure の仮想マシンを作成してデプロイされた VM の URL を返します。 関数は、前提条件を設定しを呼び出して、 **New-azurevm**関数 (Azure モジュール) 新しい仮想マシンを作成します。 |
| 追加 AzureVMEndpoints |仮想マシンに新しい入力エンドポイントを追加し、新しいエンドポイントを仮想マシンを返します。 |
| 追加 AzureVMStorage |現在のサブスクリプションには、新しい Azure ストレージ アカウントを作成します。 アカウントの名前"devtest"の後に一意の英数字の文字列で始まります。 新しいストレージ アカウントの名前を返します。 場所またはアフィニティ グループを新しいストレージ アカウントのいずれかを指定します。 |
| 追加 AzureWebsite |指定した名前と場所を持つ web サイトを作成します。 この関数を呼び出して、 **New-azurewebsite** Azure モジュールの関数。 サブスクリプションは、指定した名前の web サイトをまだ含まれていない、この関数は、web サイトを作成し、web サイト オブジェクトを返します。 返しますそれ以外の場合、`$null`します。 |
| バックアップ サブスクリプション |現在の Azure サブスクリプションを保存、`$Script:originalSubscription`スクリプト スコープの変数。 この関数は、現在の Azure サブスクリプションを保存します (によって取得`Get-AzureSubscription -Current`) とそのストレージ アカウント、およびこのスクリプトによって変更されたサブスクリプション (変数に格納されている`$UserSpecifiedSubscription`) とそのストレージ アカウントをスクリプト スコープにします。 値を保存することによって、使用できる関数の場合など`Restore-Subscription`、現在の状態が変更された場合、元の現在のサブスクリプションとストレージ アカウントを現在の状態に復元します。 |
| 検索 AzureVM |指定された Azure 仮想マシンを取得します。 |
| Format-devtestmessagewithtime |日付と時刻、メッセージを先頭に追加します。 この関数は、エラー ストリームに書き込まれたメッセージに適しています。 |
| Get AzureSQLDatabaseConnectionString |Azure SQL database に接続する接続文字列をアセンブルします。 |
| Get-azurevmstorage |名前のパターンでは、最初のストレージ アカウントの名前を返します"devtest *"(大文字と小文字は区別されません) で指定された場所またはアフィニティ グループ。場合、"devtest*"ストレージ アカウントが場所またはアフィニティ グループと一致しません、関数は無視されます。 場所またはアフィニティ グループを指定します。 |
| Get MSDeployCmd |MsDeploy.exe ツールを実行するコマンドを返します。 |
| 新しい AzureVMEnvironment |検索または JSON 構成ファイル内の値に一致するサブスクリプションの仮想マシンを作成します。 |
| 発行 WebPackage |使用して MsDeploy.exe および web パッケージを公開します。Zip ファイルを web サイトにリソースをデプロイします。 この関数は、任意の出力を生成しません。 MSDeploy.exe の呼び出しに失敗した場合、関数が例外をスローします。 さらに詳しい出力を取得する、 **-Verbose**オプション。 |
| 発行 WebPackageToVM |パラメーターの値を検証してから、 **Publish-webpackage**関数。 |
| 読み取り ConfigFile |JSON 構成ファイルを検証し、選択した値のハッシュ テーブルを返します。 |
| 復元サブスクリプション |現在のサブスクリプションを元のサブスクリプションにリセットします。 |
| Test-azuremodule |返します`$true`場合は、インストールされている Azure モジュールのバージョンが 0.7.4 以降。 返します`$false`場合は、モジュールがインストールされていないか、以前のバージョンです。 この関数には、パラメーターがありません。 |
| テスト AzureModuleVersion |返します`$true`場合は、Azure モジュールのバージョンが 0.7.4 以降。 返します`$false`場合は、モジュールがインストールされていないか、以前のバージョンです。 この関数には、パラメーターがありません。 |
| テスト HttpsUrl |入力 URL を System.Uri オブジェクトに変換します。 返します`$True`URL は絶対値であり、スキームが https の場合。 返します`$false`URL が相対 url と、そのスキームが HTTPS でないまたは入力文字列を URL に変換できません。 |
| テストのメンバー |返します`$true`プロパティまたはメソッドがオブジェクトのメンバーである場合。 それ以外の場合、`$false` を返します。 |
| 書き込み ErrorWithTime |現在の時刻をプレフィックスとしてエラー メッセージを書き込みます。 この関数を呼び出して、 **Format-devtestmessagewithtime**前に、メッセージをエラー ストリームに書き込む前に時刻を付加する関数。 |
| 書き込み HostWithTime |ホスト プログラムにメッセージを書き込みます (**Write-host**) 現在の時刻が付きます。 ホスト プログラムへの書き込み結果が異なります。 ほとんどのプログラム ホストする Windows PowerShell は、標準出力にこれらのメッセージを記述します。 |
| 書き込み VerboseWithTime |現在の時刻をプレフィックスとして詳細メッセージを書き込みます。 呼び出すので、 **Write-verbose**でスクリプトが実行されるときにのみ、メッセージが表示されます、 **Verbose**パラメーターか、 **VerbosePreference** に優先順位が設定されています。**引き続き**します。 |

**発行 WebApplication**

| 関数名 | 説明 |
| --- | --- |
| 新しい AzureWebApplicationEnvironment |Web サイトまたは仮想マシンなどの Azure リソースを作成します。 |
| 新しい WebDeployPackage |この関数は実装されていません。 コマンドは、プロジェクトをビルドするには、この関数を追加することができます。 |
| 発行 AzureWebApplication |Azure に web アプリケーションを発行します。 |
| 発行 WebApplication |作成し、Web アプリ、仮想マシン、SQL データベース、および Visual Studio web プロジェクト用のストレージ アカウントを展開します。 |
| Web アプリケーションのテスト |この関数は実装されていません。 コマンドは、アプリケーションをテストするには、この関数を追加することができます。 |

## <a name="next-steps"></a>次の手順
PowerShell スクリプトの読み取りの詳細について[Windows PowerShell でのスクリプティング](https://technet.microsoft.com/library/bb978526.aspx)で他の Azure PowerShell スクリプトを参照してくださいと、[スクリプト センター](https://azure.microsoft.com/documentation/scripts/)します。
