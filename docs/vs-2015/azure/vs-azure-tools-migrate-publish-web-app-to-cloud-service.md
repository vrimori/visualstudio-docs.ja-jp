---
title: 移行および Visual Studio から Azure クラウド サービスへの Web アプリケーションを発行する方法 |Microsoft Docs
description: 移行および Visual Studio を使用して、web アプリケーションを Azure クラウド サービスを発行する方法について説明します
author: ghogen
manager: douge
ms.assetid: 9394adfd-a645-4664-9354-dd5df08e8c91
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: c122b54a4e22285678d13213cc73d6492baba629
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003042"
---
# <a name="how-to-migrate-and-publish-a-web-application-to-an-azure-cloud-service-from-visual-studio"></a>方法: Visual Studio から Azure クラウド サービスに Web アプリケーション移行および発行

のホスティング サービスの利点と Azure の機能をスケーリングするには、移行および Azure クラウド サービスに web アプリケーションを展開する可能性があります。 最小限の変更のみが必要です。 この記事では、クラウド サービスのみへのデプロイについて説明しますApp Service では、次を参照してください。 [Azure App Service で web アプリのデプロイ](/azure/app-service/app-service-deploy-local-git)します。

> [!Important]
> この移行は、特定の ASP.NET、Silverlight、WCF、および WCF ワークフロー プロジェクトのみサポートされます。 ASP.NET Core プロジェクトはサポートされません。 参照してください[サポートされているプロジェクト テンプレート](#supported-project-templates)します。

## <a name="migrate-a-project-to-cloud-services"></a>プロジェクトのクラウド サービスを移行します。

1. Web アプリケーション プロジェクトを右クリックして**変換 > Microsoft Azure クラウド サービス プロジェクトに変換**します。 (Web ロール プロジェクトをソリューションに既にある場合に、このコマンドが表示されないことに注意してください)。
1. Visual Studio では、必要な web ロールを含むソリューションでのクラウド サービス プロジェクトを作成します。 このプロジェクトの名前は、サフィックスを付加したでアプリケーション プロジェクトとして、同じ`.Azure`します。
1. Visual Studio にも設定、**ローカル コピー** MVC 2、MVC 3、MVC 4、および Silverlight ビジネス アプリケーションに必要なすべてのアセンブリを true に設定します。 このプロパティは、これらのアセンブリを展開に使用されるサービス パッケージに追加します。

   > [!Important]
   > その他のアセンブリまたはこの web アプリケーションに必要なファイルがある場合は、これらのファイルのプロパティを手動で設定する必要があります。 これらのプロパティを設定する方法については、次を参照してください。[サービス パッケージにファイルを含める](#include-files-in-the-service-package)します。

### <a name="errors-and-warnings"></a>エラーと警告

警告またはエラーが発生するは、アセンブリの不足など、Azure にデプロイする前に解決する問題を示しています。

エラーが発生した場合は、コンピューティング エミュレーターを使用してローカルで実行、または Azure に発行するアプリケーションを作成する、可能性があります:「指定されたパス、ファイル名、またはその両方が長すぎます」。 このエラーは、Azure プロジェクトの完全修飾名の長さが 146 文字を超えていることを示します。 この問題が解決するには、短いパスを持つ別のフォルダーにソリューションを移動します。

すべての警告をエラーとして処理する方法の詳細については、次を参照してください。 [Visual Studio で Azure クラウド サービス プロジェクトを構成する](vs-azure-tools-configuring-an-azure-project.md)します。

### <a name="test-the-migration-locally"></a>移行をローカルでのテストします。

1. Visual Studio で**ソリューション エクスプ ローラー**を追加したクラウド サービス プロジェクトを右クリックし、**スタートアップ プロジェクトとして設定**します。
1. 選択**デバッグ > [デバッグ開始]** Azure デバッグ環境を起動するには、(F5)。 具体的には、この環境には、さまざまな Azure サービスのエミュレーションが用意されています。

### <a name="use-an-azure-sql-database-for-your-application"></a>Azure SQL Database をアプリケーションを使用します。

を、オンプレミスの SQL Server データベースを使用する web アプリケーションの接続文字列がある場合は、代わりに Azure SQL Database にデータベースの移行し、接続文字列を更新する必要があります。 このプロセスのガイダンスについては、次のトピックを参照してください。

- [SQL Server データベースのクラウドで SQL Database への移行](/azure/sql-database/sql-database-cloud-migrate)
- [.NET を使用して (C#) 接続し、クエリに Visual Studio および Azure SQL データベースで](/azure/sql-database/sql-database-connect-query-dotnet-visual-studio)します。

## <a name="publish-the-application-to-azure-cloud-service"></a>Azure クラウド サービスにアプリケーションを発行します。

1. 必要なクラウド サービスとストレージ アカウントで作成、Azure サブスクリプションの説明に従って[の発行または Visual Studio から Azure アプリケーションをデプロイするための準備](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)します。
1. Visual Studio では、アプリケーション プロジェクトを右クリックして**Microsoft Azure に公開しています.** (これは、[発行] コマンドからは異なります)。
1. **Azure アプリケーションの発行**アカウントを使用して、Azure サブスクリプションにサインインし、選択、表示される **[次へ] >** します。
1. **設定 > の一般的な設定**タブで、ターゲットのクラウド サービスからの選択、**クラウド サービス**と共に、環境と構成のドロップダウン リスト。 
1. **設定 > 詳細設定**を選択し、ストレージ アカウントを選択します。 **次へ >** します。
1. **診断**、Application Insights に情報を送信するかどうかを選択します。
1. 選択 **[次へ] >** 概要を表示するを選択し、**発行**の展開を開始します。
1. Visual Studio では、進行状況を追跡するアクティビティ ログ ウィンドウが開きます。

    ![VST_AzureActivityLog](./media/vs-azure-tools-migrate-publish-web-app-to-cloud-service/IC744149.png)

1. (省略可能)デプロイ プロセスをキャンセルするには、アクティビティ ログの行項目を右クリックし、選択**キャンセルし、削除**します。 このコマンドは、展開プロセスを停止し、Azure からデプロイ環境を削除します。 注: デプロイされた後は、このデプロイ環境を削除するにする必要がありますを使用して、 [Azure portal](https://portal.azure.com)します。
1. (省略可能)Visual Studio が自動的にデプロイ環境を表示して、ロール インスタンスが起動すると、**サーバー エクスプ ローラー > クラウド サービス**ノード。 ここからは、個々 のロール インスタンスの状態を表示できます。
1. デプロイ後に、アプリケーションにアクセスする状態のときにデプロイの横の矢印を選択**完了**に表示されます、 **Azure アクティビティ ログ**URL と共にします。 Azure から特定の種類の web アプリケーションを起動する方法の詳細については、次の表を参照してください。

## <a name="using-the-compute-emulator-and-starting-application-in-azure"></a>コンピューティング エミュレーターを使用して、Azure でアプリケーションを起動

すべてのアプリケーションの種類を選択して、Visual Studio デバッガーに接続されているブラウザーで起動できます**デバッグ > [デバッグ開始]** (F5)。 空の ASP.NET Web アプリケーション プロジェクトでは、まず追加、`.aspx`アプリケーションでページし、web プロジェクトのスタート ページとして設定します。

次の表では、Azure でアプリケーションを起動する方法の詳細を示します。

   | Web アプリケーションの種類 | Azure で実行されています。 |
   | --- | --- | --- |
   | ASP.NET Web アプリケーション<br/>(MVC 2、MVC 3、MVC 4 を含む) | 内の URL を選択、**展開**タブに移動して、 **Azure アクティビティ ログ**します。 |
   | 空の ASP.NET Web アプリケーション | 既定値がある場合`.aspx`、アプリケーションのページで URL を選択、**展開**タブに移動して、 **Azure アクティビティ ログ**。 別のページに移動するには、ブラウザーで、次の形式の URL を入力します。 `<deployment_url>/<page_name>.aspx` |
   | Silverlight アプリケーション<br/>Silverlight ビジネス アプリケーション<br/>Silverlight ナビゲーション アプリケーション | 次の URL 形式を使用して、アプリケーションの特定のページに移動します。 `<deployment_url>/<page_name>.aspx` |
    WCF サービス アプリケーション<br/>WCF ワークフロー サービス アプリケーション | 設定、`.svc`スタート ページとして、WCF サービス プロジェクトのファイル。 移動します `<deployment_url>/<service_file>.svc` |
   | ASP.NET 動的エンティティ<br/>ASP.NET 動的データ Linq to SQL | 次のセクションで説明した、接続文字列を更新します。 移動し、`<deployment_url>/<page_name>.aspx`します。 Linq to SQL での Azure SQL database を使用する必要があります。 |

## <a name="update-a-connection-string-for-aspnet-dynamic-entities"></a>ASP.NET 動的エンティティの接続文字列を更新します。

1. (#Use-an-azuresql-database-for-your-application) で前述したように、ASP.NET 動的エンティティ web アプリケーションの SQL Azure データベースを作成します。
1. テーブルと、Azure portal からこのデータベースに必要なフィールドを追加します。
1. 内の接続文字列を指定、`web.config`次の形式でファイルを開き、ファイルを保存します。

    ```xml
    <addname="tempdbEntities"connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;data source=<server name>\SQLEXPRESS;initial catalog=<database name>;integrated security=True;multipleactiveresultsets=True;App=EntityFramework&quot;"providerName="System.Data.EntityClient"/>
    ```

    更新プログラム、 *connectionString*値の次のように、SQL Azure データベースの ADO.NET 接続文字列に置き換えます。

    ```xml
    XMLCopy<addname="tempdbEntities"connectionString="metadata=res://*/Model1.csdl|res://*/Model1.ssdl|res://*/Model1.msl;provider=System.Data.SqlClient;provider connection string=&quot;Server=tcp:<SQL Azure server name>.database.windows.net,1433;Database=<database name>;User ID=<user name>;Password=<password>;Trusted_Connection=False;Encrypt=True;multipleactiveresultsets=True;App=EntityFramework&quot;"providerName="System.Data.EntityClient"/>
    ```

## <a name="supported-project-templates"></a>サポートされているプロジェクト テンプレート

移行およびクラウド サービスに発行するアプリケーションは、次の表に、テンプレートのいずれかを使用する必要があります。 ASP.NET Core がサポートされていません。

| テンプレート グループ | プロジェクト テンプレート |
| --- | --- |
| Web | ASP.NET Web アプリケーション (.NET Framework) |
| Web | ASP.NET MVC 2 Web アプリケーション |
| Web | ASP.NET MVC 3 Web アプリケーション |
| Web | ASP.NET mvc 4 Web アプリケーション |
| Web | 空の ASP.NET Web アプリケーション (またはサイト) |
| Web | ASP.NET MVC 2 の空の Web アプリケーション |
| Web | ASP.NET 動的データ エンティティ Web アプリケーション |
| Web | ASP.NET 動的データ Linq to SQL Web アプリケーション |
| Silverlight | Silverlight アプリケーション |
| Silverlight | Silverlight ビジネス アプリケーション |
| Silverlight | Silverlight ナビゲーション アプリケーション |
| WCF | WCF サービス アプリケーション |
| WCF | WCF ワークフロー サービス アプリケーション |
| ワークフロー | WCF ワークフロー サービス アプリケーション |

## <a name="next-steps"></a>次の手順

- [発行または Visual Studio からの Azure アプリケーションをデプロイするためを準備します。](vs-azure-tools-cloud-service-publish-set-up-required-services-in-visual-studio.md)
- [名前付き認証資格情報を設定する](vs-azure-tools-setting-up-named-authentication-credentials.md)します。
