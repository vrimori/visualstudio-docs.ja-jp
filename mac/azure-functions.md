---
title: Azure Functions の概要
description: Visual Studio for Mac での Azure Functions の使用。
author: asb3993
ms.author: amburns
ms.date: 05/06/2018
ms.topic: article
ms.technology: vs-ide-install
ms.assetid: 25CD47A4-5B32-4734-8EF3-E24A02AABF29
ms.openlocfilehash: 5d787efbd09ad7f2d4a1f5f72b8f1493d8c6c587
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
ms.locfileid: "33870413"
---
# <a name="introduction-to-azure-functions"></a>Azure Functions の概要

Azure Functions を利用すると、クラウドでイベント ドリブンのコード スニペットつまり関数を作成できます。インフラストラクチャを明示的にプロビジョニングまたは管理する必要はありません。 Azure Functions について詳しくは、[Azure Functions のドキュメント](https://docs.microsoft.com/azure/azure-functions/)をご覧ください。

## <a name="requirements"></a>必要条件

Azure Function ツールは **Visual Studio for Mac 7.5** に付属しています。

関数を作成して展開するには、Azure サブスクリプションも必要です。Azure サブスクリプションは [https://azure.com/free](https://azure.com/free) から無料で入手できます。

## <a name="creating-your-first-azure-functions-project"></a>初めての Azure Functions プロジェクトの作成

1. Visual Studio for Mac で **[ファイル] > [新しいソリューション]** の順に選びます。 
2. [新しいプロジェクト] ダイアログで、**[クラウド] > [全般]** から Azure Functions テンプレートを選び、**[次へ]** をクリックします。

    ![Azure Functions のオプションが表示されている [新しいプロジェクト] ダイアログ](media/azure-functions-image1.png)

3. **[プロジェクト名]** を入力し、**[作成]** を選びます。

Visual Studio for Mac によって、既定の HttpTrigger 関数が含まれる .NET Standard プロジェクトが作成されます。 また、さまざまな **AzureWebJobs** パッケージと、**Newtonsoft.Json** パッケージへの NuGet 参照も含まれます。

![テンプレートからの新しい Azure Function が表示されている Visual Studio for Mac エディター](media/azure-functions-newproj.png)

新しいプロジェクトには次のファイルが含まれています。

* **HttpTrigger.cs** – このクラスには、HTTP によってトリガーされる関数の定型コードが含まれます。 関数名を保持する **FunctionName** 属性と、関数が HTTP 要求によってトリガーされることを指定するトリガー属性 **HttpTrigger** が含まれます。 関数のメソッドについて詳しくは、「[Azure Functions C# 開発者向けリファレンス](https://docs.microsoft.com/azure/azure-functions/functions-dotnet-class-library)」をご覧ください。
* **host.json** – このファイルでは、Functions ホストのグローバル構成オプションが記述されています。 ファイルの例と、このファイルで使用可能な設定については、「[Azure Functions の host.json のリファレンス](https://docs.microsoft.com/azure/azure-functions/functions-host-json)」をご覧ください。
* **local.settings.json** – このファイルには、関数をローカルで実行するためのすべての設定が含まれます。 これらの設定は、Azure Functions Core Tools によって使用されます。 詳しくは、Azure Functions Core Tools に関する記事の「[ローカル設定ファイル](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local#local-settings-file)」をご覧ください。

Visual Studio for Mac で新しい Azure Functions プロジェクトが作成されたので、ローカル コンピューターから既定の HTTP によってトリガーされる関数をテストできます。

<!--
## Create an Azure storage account

[Describe why this step is necessary and what it does]

1. Log on to your account at [https://portal.azure.com](https://portal.azure.com).
2. Under the **Favorites** section, located on the left of the screen, select **Storage Accounts**:
    ![]()
3. Select **Add** to create a new storage account:
    ![]()
4. Enter a globally unique name for the **Name** and reuse it for the **Resource group**. You can keep all the other items as their default.
    ![]()
5. Click **Create**. It might take a few minutes to create the storage account. You'll get a notification once it has been successfully created.
6. Select the **Go to resource** button from the notification:
    ![]()
-->

## <a name="testing-the-function-locally"></a>関数のローカルなテスト

Visual Studio for Mac での Azure Functions のサポートを使うと、開発用のローカル コンピューター上で関数をテストおよびデバッグすることができます。

1. 関数をローカルにテストするには、Visual Studio for Mac で **[実行]** ボタンをクリックします。

    ![Visual Studio for Mac のデバッグ開始ボタン](media/azure-functions-run.png)

1. プロジェクトを実行すると、Azure Functions でのローカルなデバッグが開始し、次の図に示すように、新しいターミナル ウィンドウを開きます。 

    ![関数の出力が表示されているターミナル ウィンドウ](media/azure-functions-terminal.png) 

    出力から URL をコピーします。

3. HTTP 要求の URL をブラウザーのアドレス バーに貼り付けます。 URL の末尾にクエリ文字列 `?name=<yourname>` を追加し、要求を実行します。 次の図は、関数によって返されるローカル GET 要求に対するブラウザーでの応答です。

    ![ブラウザーでの HTTP 要求](media/azure-functions-httpreq.png)

## <a name="creating-a-new-function"></a>新しい関数の作成

関数テンプレートを使用すると、最も一般的なトリガーとテンプレートを使って、新しい関数をすばやく作成できます。 新しく作成した Azure Functions プロジェクトには、HttpTrigger 関数が自動的に含まれます。 別の種類の関数を作成するには、次のようにします。

1. **HttpTrigger.cs** ファイルを右クリックして **[削除]** を選ぶことで、このファイルを削除します。 次のアラートから **[削除]** を選び、プロジェクトからファイルを削除します。

    ![ファイルをプロジェクトから削除するためのダイアログ](media/azure-functions-remove.png)

2. 新しい関数を追加するには、プロジェクト名を右クリックして、**[追加] > [関数の追加]** を選びます。

    ![新しい関数を追加するコンテキスト アクション](media/azure-functions-addnew.png)

3. **[新しい Azure Function ]** ダイアログで、必要な関数を選びます。

    ![[新しい Azure Function ] ダイアログ](media/azure-functions-newfunction.png)

    次のセクションでは、Azure Function テンプレートの一覧を示します。

## <a name="available-function-templates"></a>使用可能な関数テンプレート

- **HTTP** – HTTP 要求を使って、コードの実行をトリガーします。 次の HTTP トリガーに対する明示的なテンプレートがあります。
    - Http GET CRUD
    - Http POST CRUD
    - パラメーター付き HTTP トリガー
    - HTTP トリガー
- **タイマー**: 定義されているスケジュールに基づいて、クリーンアップまたは他のバッチ タスクを実行します。 このテンプレートは名前とスケジュールの 2 つのフィールドを受け取ります。6 フィールドの CRON 式です。 詳しくは、[タイマーについての Azure Functions の記事](https://docs.microsoft.com/azure/azure-functions/functions-create-scheduled-function)をご覧ください。
- **GitHub トリガー** – GitHub リポジトリで発生するイベントに応答します。 詳しくは、[GitHub についての Azure Functions の記事](https://docs.microsoft.com/azure/azure-functions/functions-create-github-webhook-triggered-function)をご覧ください。
    - GitHub コメンター – この関数は、問題またはプル要求の GitHub webhook を受信してコメントを追加すると実行されます。
    - GitHub WebHook – この関数は、GitHub webhook を受信すると実行されます
- **BLOB トリガー** – Azure Storage Blob がコンテナーに追加されるとそれを処理します。 このテンプレートは、関数名だけでなく、パスと接続のプロパティも受け取ります。 パス プロパティは、トリガーが監視するストレージ アカウント内のパスです。 接続アカウントは、ストレージ アカウント接続文字列が含まれるアプリ設定の名前です。 詳しくは、[Blob Storage についての Azure Functions の記事](https://docs.microsoft.com/azure/azure-functions/functions-create-storage-blob-triggered-function)をご覧ください。
- **キュー トリガー** – これは、Azure Storage キューに届いたメッセージに応答する関数です。 このテンプレートは、関数名だけでなく、**パス** (メッセージが読み取られるキューの名前) とストレージ アカウント**接続** (ストレージ アカウント接続文字列を含むアプリ設定の名前) を受け取ります。 詳しくは、[Queue Storage についての Azure Functions の記事](https://docs.microsoft.com/azure/azure-functions/functions-create-storage-queue-triggered-function)をご覧ください。
- **汎用 webhook** – これは、webhook をサポートするサービスから要求を受信するたびに実行される単純な関数です。 詳しくは、[汎用 webhook についての Azure Functions の記事](https://docs.microsoft.com/azure/azure-functions/functions-create-generic-webhook-triggered-function)をご覧ください。
- **イメージ リサイザー** – この関数は、コンテナーに BLOB が追加されるたびに異なるサイズのイメージを作成します。 このテンプレートは、トリガーに対するパスと接続文字列、小さいイメージ出力、および中くらいのイメージ出力を受け取ります。
- **SAS トークン** – この関数は、特定の Azure Storage コンテナーおよび BLOB 名に対して SAS トークンを生成します。 このテンプレートは、関数名だけでなく、パスと接続のプロパティも受け取ります。 パス プロパティは、トリガーが監視するストレージ アカウント内のパスです。 接続アカウントは、ストレージ アカウント接続文字列が含まれるアプリ設定の名前です。 **アクセス権**も設定する必要があります。 承認レベルは、関数に API キーが必要かどうか、および使用するキーを制御します。関数は関数キーを使います。管理者は、マスター キーを使います。 詳しくは、「[C# Azure Function for generating SAS tokens](https://azure.microsoft.com/resources/samples/functions-dotnet-sas-token/)」(SAS トークンを生成するための C# Azure Function) サンプルをご覧ください。
- **Durable Functions オーケストレーション** – Durable Functions を使うと、サーバーレス環境でステートフル関数を記述できます。 この拡張機能は、状態、チェックポイント、および再起動を自動的に管理します。 詳しくは、[Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)に関する Azure Functions ガイドをご覧ください。