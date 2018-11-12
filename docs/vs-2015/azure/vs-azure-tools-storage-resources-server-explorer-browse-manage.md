---
title: 参照し、サーバー エクスプ ローラーを使用してストレージ リソースの管理 |Microsoft Docs
description: 参照して、サーバー エクスプ ローラーを使用して記憶域リソースを管理します。
author: ghogen
manager: douge
assetId: 658dc064-4a4e-414b-ae5a-a977a34c930d
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/24/2017
ms.author: ghogen
ms.openlocfilehash: 00229cd88ddcab4d2d59ae40202620c374415e4b
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2018
ms.locfileid: "51003049"
---
# <a name="browse-and-manage-storage-resources-by-using-server-explorer"></a>サーバー エクスプローラーを使用したストレージ リソースの参照と管理

[!INCLUDE [storage-try-azure-tools](./includes/storage-try-azure-tools.md)]

## <a name="overview"></a>概要

Azure Tools for Microsoft Visual Studio をインストールした場合は、Azure のストレージ アカウントから blob、キュー、およびテーブル データを表示できます。 Azure**ストレージ**サーバー エクスプ ローラー ノードには、ローカル ストレージ エミュレーター アカウントと、その他の Azure ストレージ アカウント内にあるデータが表示されます。

メニュー バーで、Visual Studio で、サーバー エクスプ ローラーを表示する選択**ビュー** > **サーバー エクスプ ローラー**します。 **ストレージ**ノードには、各 Azure サブスクリプションまたはに接続している証明書の下に存在するストレージ アカウントのすべてが表示されます。 ストレージ アカウントが表示されない場合は、次の手順で追加できます[この記事で後述](#add-storage-accounts-by-using-server-explorer)します。

Azure SDK 2.7 以降、Azure リソースの管理を表示したり Cloud Explorer を使用することができますも。 詳細については、次を参照してください。[クラウド エクスプ ローラーで管理する Azure リソース](vs-azure-tools-resources-managing-with-cloud-explorer.md)します。

## <a name="view-and-manage-storage-resources-in-visual-studio"></a>表示し、Visual Studio での記憶域リソースの管理

サーバー エクスプ ローラーでは、blob、キュー、およびテーブルの一覧が、ストレージ エミュレーター アカウントで自動的に表示されます。 サーバー エクスプ ローラーでストレージ エミュレーター アカウントが一覧表示、**ストレージ**ノードとして、**開発**ノード。

ストレージ エミュレーター アカウントのリソースを表示するには、展開、**開発**ノード。 展開したときに、ストレージ エミュレーターを起動されていないかどうか、**開発**ノードが自動的に開始します。 このプロセスは数秒をかかります。 ストレージ エミュレーターの起動中に、Visual Studio の他の領域で作業を続行できます。

ストレージ アカウントのリソースを表示するには、表示されているサーバー エクスプ ローラーでストレージ アカウントのノードを展開**Blob**、**キュー**、および**テーブル**ノード。

## <a name="work-with-blob-resources"></a>Blob リソースを操作します。

**Blob**ノードが選択したストレージ アカウントのコンテナーの一覧を表示します。 Blob コンテナーには、blob のファイルが含まれているし、フォルダーおよびサブフォルダーに、これらの blob を整理することができます。 詳細については、次を参照してください。 [.NET から Blob ストレージを使用する方法](/azure/storage/blobs/storage-dotnet-how-to-use-blobs)します。

### <a name="to-create-a-blob-container"></a>Blob コンテナーを作成するには

1. ショートカット メニューを開き、 **Blob**ノードをクリックして**Blob コンテナーの作成**です。
1. **Blob コンテナーの作成** ダイアログ ボックスに、新しいコンテナーの名前を入力します。  
1. または、キーボードで enter キーを押しますでは、をクリックしてしたり、blob コンテナーを保存、名前フィールドの外側をタップすることができます。

   > [!NOTE]
   > Blob コンテナーの名前は、数字 (0 ~ 9) または小文字 (a ~ z) で始める必要があります。

### <a name="to-delete-a-blob-container"></a>Blob コンテナーを削除するには

削除、および選択する blob コンテナーのショートカット メニューを開き**削除**します。

### <a name="to-display-a-list-of-the-items-in-a-blob-container"></a>Blob コンテナー内の項目の一覧を表示するには

一覧で、blob コンテナー名のショートカット メニューを開きを選択します**オープン**します。

Blob コンテナーの内容を表示すると、blob コンテナー ビューと呼ばれるタブに表示されます。

![Blob コンテナー ビュー](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC749016.png)

Blob に対する次の操作を実行するには、blob コンテナーのビューの右上隅のボタンを使用します。

* フィルター値を入力し、それを適用します。
* コンテナー内の blob の一覧を更新します。
* ファイルをアップロードします。
* Blob を削除します。 (ファイルを削除する blob コンテナーから削除されません、基になるファイル。 だけから削除される blob コンテナー。)
* Blob を開きます。
* Blob をローカル コンピューターに保存します。

### <a name="to-create-a-folder-or-subfolder-in-a-blob-container"></a>Blob コンテナーにフォルダーまたはサブフォルダーを作成するには

1. Cloud Explorer で blob コンテナーを選択します。 コンテナー ウィンドウで、選択、 **Blob のアップロード**ボタンをクリックします。

1. **新しいファイルのアップロード**ダイアログ ボックスで、**参照**、アップロードするファイルを指定するボタンをクリックし、フォルダーの名前を入力し、**フォルダー (省略可)** ボックス。

   ![Blob のフォルダーにファイルをアップロードします。](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766037.png)

   同じ手順に従って、コンテナーのフォルダーにサブフォルダーを追加できます。 フォルダー名を指定しない場合は、ファイルが blob コンテナーの最上位にアップロードされます。 コンテナー内の指定したフォルダーにファイルが表示されます。

   ![Blob コンテナーに追加されたフォルダー](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766038.png)

1. フォルダーをダブルクリックするか、フォルダーの内容を表示するには Enter を選択します。 コンテナーのフォルダーの場合は、することができますに戻り、コンテナーのルートを選択して、**親ディレクトリを開く**(矢印) ボタンをクリックします。

### <a name="to-delete-a-container-folder"></a>コンテナーのフォルダーを削除するには

フォルダー内のすべてのファイルを削除します。

Blob コンテナー内のフォルダーは仮想フォルダーであるため、空のフォルダーを作成することはできません。 また、そのファイルの内容を削除するフォルダーを削除することはできませんが、代わりに、フォルダー自体を削除するフォルダーの内容全体を削除する必要があります。

### <a name="to-filter-blobs-in-a-container"></a>コンテナー内の blob をフィルター処理するには

共通のプレフィックスを指定することによって表示される blob をフィルター処理することができます。

たとえば、プレフィックスを入力する**こんにちは**クリックしてフィルター テキスト ボックスで、 **Execute** (**!**) ボタン、「こんにちは」で始まる blob のみが表示されます。

![フィルター テキスト ボックス](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC519076.png)

フィルター テキスト ボックスは、大文字小文字を区別し、ワイルドカード文字によるフィルター処理をサポートしていません。 Blob はプレフィックスでのみフィルター処理できます。 プレフィックスは、仮想階層内の blob を整理する区切り記号を使用している場合、区切り記号を含めることができます。 たとえば、プレフィックスでフィルター処理"HelloFabric/"がその文字列で始まるすべての blob を返します。

### <a name="to-download-blob-data"></a>Blob データをダウンロードするには

クラウド エクスプ ローラーで、次のメソッドのいずれかの手順に従います。

* 1 つまたは複数の blob のショートカット メニューを開きを選択します**オープン**します。
* Blob 名を選択し、、**オープン**ボタンをクリックします。
* Blob 名をダブルクリックします。

Blob のダウンロードの進行状況が表示されます、 **Azure アクティビティ ログ**ウィンドウ。

Blob は、そのファイルの種類の既定のエディターで開きます。 オペレーティング システムがファイルの種類を認識しない場合は、ローカルにインストールされたアプリケーションで、ファイルが開きます。 それ以外の場合、blob のファイルの種類に適したアプリケーションを選択するように求められます。 Blob をダウンロードするときに作成されるローカル ファイルは読み取り専用とマークされます。

Blob データはローカルにキャッシュし、Azure Blob storage 内の blob の最終更新時刻と照合します。 最後にダウンロードされたので、blob が更新された場合、もう一度ダウンロードされます。 それ以外の場合、blob は、ローカル ディスクから読み込まれます。

既定では、blob が一時ディレクトリにダウンロードされます。 特定のディレクトリに blob をダウンロードする選択した blob 名のショートカット メニューを開くし、選択**付けて**します。 この方法で blob を保存するときに blob ファイルが開かれていないと、ローカル ファイル読み取り/書き込み属性が作成します。

### <a name="to-upload-blobs"></a>Blob をアップロードするには

Blob をアップロードするには、選択、 **Blob のアップロード** ボタン、コンテナーを開き、blob コンテナー ビューに表示する場合。

1 つまたは複数のファイルをアップロードすることができ、任意の種類のファイルをアップロードすることができます。 **Azure アクティビティ ログ**ウィンドウには、アップロードの進行状況が表示されます。 Blob データを操作する方法の詳細については、次を参照してください。 [.NET で Azure Blob storage を使用する方法](http://go.microsoft.com/fwlink/p/?LinkId=267911)します。

### <a name="to-view-logs-transferred-to-blobs"></a>Blob に転送されたログを表示するには

Azure 診断を使用して、Azure アプリケーションからデータをログには、ストレージ アカウントにログを転送した場合は、Azure がこれらのログ用に作成されたコンテナーが表示されます。 サーバー エクスプ ローラーでこれらのログを表示するという問題は、特に Azure にデプロイされた場合のアプリケーションの問題を識別するために簡単です。

Azure 診断の詳細については、次を参照してください。 [Azure 診断を使用してログ データの収集](https://msdn.microsoft.com/library/azure/gg433048.aspx)します。

### <a name="to-get-the-url-for-a-blob"></a>Blob の URL を取得するには

Blob のショートカット メニューを開き、選択**URL のコピー**します。

### <a name="to-edit-a-blob"></a>Blob を編集するには

Blob を選択し、選択、 **Blob を開く**ボタンをクリックします。

ファイルは一時的な場所にダウンロードされ、ローカル コンピューターで開かれます。 変更を行った後は、blob をアップロードします。

## <a name="work-with-queue-resources"></a>キュー リソースを操作します。

ストレージ サービスのキューは、Azure ストレージ アカウントでホストされます。 それらを使用して、メッセージ パッシング機構と他のサービスと通信するサービスの役割をクラウドにしたりすることができます。 クラウド サービスと外部クライアントの web サービス経由では、キューをプログラムでアクセスできます。 キューは、Visual Studio でサーバー エクスプ ローラーを使用して直接アクセスすることもできます。

キューを使用するクラウド サービスを開発する際に、Visual Studio を使用してキューを作成し、開発やテスト、コードに対話的に操作をする可能性があります。

サーバー エクスプ ローラーでストレージ アカウント内のキューを表示、作成しキューの削除、そのメッセージを表示するキューを開くしてメッセージをキューに追加します。 表示するためのキューを開くし、個々 のメッセージを表示することができます、左上隅にあるボタンを使用して、キューで、次の操作を行うことができます。

* キューのビューを更新します。
* キューにメッセージを追加します。
* 最上位のメッセージをデキューします。
* キュー全体をオフにします。

次の図は、2 つのメッセージを含むキューを示しています。

![キューの表示](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC651470.png)

ストレージの詳細については、キュー サービスを参照してください。 [.NET を使用して Azure Queue storage の概要](http://go.microsoft.com/fwlink/?LinkID=264702)します。 Web サービスに関する情報の記憶域サービスのキューを参照してください[キュー サービスの概念](http://go.microsoft.com/fwlink/?LinkId=264788)します。 Visual Studio を使用して、記憶域サービスのキューにメッセージを送信する方法については、次を参照してください。[記憶域サービスのキューにメッセージを送信する](https://docs.microsoft.com/azure/visual-studio/vs-storage-cloud-services-getting-started-queues)します。

> [!NOTE]
> ストレージ サービスのキューは、Azure Service Bus キューとは異なります。 Service Bus キューの詳細については、次を参照してください。 [Service Bus キュー、トピック、およびサブスクリプション](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-queues-topics-subscriptions)します。

## <a name="work-with-table-resources"></a>テーブル リソースを操作します。

Azure Table storage は、大量の構造化データを格納します。 サービスは、Azure のクラウドの内外からの認証された呼び出しを受け付ける NoSQL データストアです。 Azure のテーブルは構造化された非リレーショナル データの格納に最適です。

### <a name="to-create-a-table"></a>テーブルを作成するには

1. クラウド エクスプ ローラーで選択、**テーブル**ノードを選択し、ストレージ アカウントの**Create Table**します。
1. **Create Table**  ダイアログ ボックスに、テーブルの名前を入力します。

### <a name="to-view-table-data"></a>テーブルのデータを表示するには

1. クラウド エクスプ ローラーで開き、 **Azure**ノード、および順に開いて、**ストレージ**ノード。
1. 開きますして目的のストレージ アカウント ノードを開き、**テーブル**ストレージ アカウントのテーブルの一覧を表示するノード。
1. 表については、ショートカット メニューを開き、選択**ビュー テーブル**します。

    ![ソリューション エクスプ ローラーで Azure テーブル](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744165.png)

テーブルは、エンティティ (行に表示) と (列に表示) プロパティによって編成されています。 たとえば、次の図は、テーブル デザイナーで一覧表示されたエンティティを示します。

### <a name="to-edit-table-data"></a>テーブルのデータを編集するには

テーブル デザイナーの中には、エンティティ (単一の行) またはプロパティ (単一のセル)、ショートカット メニューを開き、クリックして**編集**します。

    ![Add or edit a table entity](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC656238.png)

1 つのテーブル内のエンティティのプロパティ (列) の同じセットが必要でないです。 表示とテーブル データを編集するのには、次の制限に注意してください。

* 表示またはバイナリ データを編集することはできません (`type byte[]`)、テーブルに格納することもできます。
* 編集することはできません、 **PartitionKey**または**RowKey**値は、azure Table storage は、その操作をサポートしないためです。
* という名前のプロパティを作成することはできません**タイムスタンプ**します。 Azure ストレージ サービスでは、その名前を持つプロパティを使用します。
* 入力した場合、 **DateTime**値、お使いのコンピューターの地域と言語設定に適した形式を従う必要があります (たとえば、/、MM/DD/YYYY HH:MM:SS [AM |PM] 米国英語の場合)。

### <a name="to-add-entities"></a>エンティティを追加するには

1. テーブル デザイナーで、選択、**エンティティの追加**ボタンをクリックします。

    ![エンティティのボタンを追加します。](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655336.png)

1. **エンティティの追加** ダイアログ ボックスの値を入力して、 **PartitionKey**と**RowKey**プロパティ。

    ![エンティティのダイアログ ボックスを追加します。](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655335.png)

    値を慎重に入力します。 エンティティを削除して再度追加しない限り、ダイアログ ボックスを閉じた後は変更できません。

### <a name="to-filter-entities"></a>エンティティをフィルター処理するには

クエリ ビルダーを使用する場合は、テーブルに表示されるエンティティのセットをカスタマイズできます。

1. クエリ ビルダーを開くには、表示するテーブルを開きます。
1. 選択、**クエリ ビルダー**テーブル ビューのツールバーのボタンをクリックします。

    **クエリ ビルダー**  ダイアログ ボックスが表示されます。 次の図は、クエリ ビルダーで構築されるクエリを示します。

    ![クエリ ビルダー](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC652231.png)
1. 完了したら、クエリの作成 ダイアログ ボックスを閉じます。 クエリの結果として得られるテキストの形式は、WCF Data Services フィルターとしてテキスト ボックスに表示されます。
1. クエリを実行するには、緑の三角形アイコンを選択します。

表示されるエンティティ データ テーブル デザイナーで入力した場合、フィルター テキスト ボックスに直接 WCF Data Services フィルター文字列をフィルターすることもできます。 この種の文字列は、SQL の WHERE 句に似ていますが、HTTP 要求としてサーバーに送信されます。 フィルター文字列を作成する方法については、次を参照してください。[テーブル デザイナー用のフィルター文字列の作成](https://docs.microsoft.com/azure/vs-azure-tools-table-designer-construct-filter-strings)です。

次の図は、有効なフィルター文字列の例を示します。

![フィルター文字列](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC655337.png)

## <a name="refresh-storage-data"></a>ストレージ データを更新します。

サーバー エクスプ ローラーに接続するか、ストレージ アカウントからデータを取得、操作かかる場合があります 1 分に完了します。 サーバー エクスプ ローラーに接続できない、操作がタイムアウトになる可能性があります。データの取得中には、Visual Studio の他の部分で作業を続行できます。 時間がかかりすぎる場合、操作をキャンセルする、**更新の中止**サーバー エクスプ ローラー ツールバーのボタンをクリックします。

### <a name="to-refresh-blob-container-data"></a>Blob コンテナーのデータを更新するには

* 選択、 **Blob**ノードの下に**ストレージ**を選び、**更新**サーバー エクスプ ローラー ツールバーのボタン。
* 表示される blob の一覧を更新する、 **Execute**ボタンをクリックします。

### <a name="to-refresh-table-data"></a>テーブルのデータを更新するには

* 選択、**テーブル**ノードの下に**ストレージ**を選び、**更新**サーバー エクスプ ローラー ツールバーのボタン。
* テーブル デザイナーに表示されるエンティティの一覧を更新する、 **Execute**テーブル デザイナーでボタンをクリックします。

### <a name="to-refresh-queue-data"></a>キューのデータを更新するには

選択、**キュー**ノードの下に**ストレージ**を選び、**更新**サーバー エクスプ ローラー ツールバーのボタン。

### <a name="to-refresh-all-items-in-a-storage-account"></a>ストレージ アカウント内のすべてのアイテムを更新するには

アカウントの名前を選択し、、**更新**サーバー エクスプ ローラー ツールバーのボタンをクリックします。

## <a name="add-storage-accounts-by-using-server-explorer"></a>サーバー エクスプ ローラーを使用してストレージ アカウントを追加します。

サーバー エクスプ ローラーを使用してストレージ アカウントを追加する 2 つの方法はあります。 ストレージ アカウントを作成するには、Azure のサブスクリプションで、または既存のストレージ アカウントをアタッチすることができます。

### <a name="to-create-a-storage-account-by-using-server-explorer"></a>サーバー エクスプ ローラーを使用してストレージ アカウントを作成するには

1. サーバー エクスプ ローラーのショートカット メニューを開き、**ストレージ**ノードをクリックして**ストレージ アカウントの作成**です。

1. **ストレージ アカウントの作成** ダイアログ ボックスで、選択するか、次の情報を入力します。

   * ストレージ アカウントを追加する Azure サブスクリプション。
   * 新しいストレージ アカウントを使用する名前です。
   * リージョンまたはアフィニティ グループ (米国西部や東アジア)。
   * など、ストレージ アカウントを使用するレプリケーションの種類ローカル冗長です。

   ![Azure storage アカウントを作成します。](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC744166.png)

1. **[作成]** を選択します。

新しいストレージ アカウントに表示される、**ストレージ**ソリューション エクスプ ローラーの一覧。

### <a name="to-attach-an-existing-storage-account-by-using-server-explorer"></a>サーバー エクスプ ローラーを使用して既存のストレージ アカウントをアタッチするには

1. サーバー エクスプ ローラーで、Azure のショートカット メニューを開き**ストレージ**ノードをクリックして**外部ストレージのアタッチ**します。

    ![既存のストレージ アカウントを追加します。](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766039.png)
1. **ストレージ アカウントの作成** ダイアログ ボックスで、選択するか、次の情報を入力します。

   * アタッチする既存のストレージ アカウントの名前。
   * 選択したストレージ アカウントのキー。 この値は、ストレージ アカウントを選択するときに通常が提供されます。 Visual Studio に、ストレージ アカウント キーを記憶する場合は、選択、**アカウント キーを記憶**チェック ボックスをオンします。
   * HTTP、HTTPS、またはカスタム エンドポイントなど、ストレージ アカウントへの接続に使用するプロトコル。 カスタム エンドポイントの詳細については、次を参照してください。[接続文字列を構成する方法](https://msdn.microsoft.com/library/azure/ee758697.aspx)します。

### <a name="to-view-the-secondary-endpoints"></a>セカンダリ エンドポイントを表示するには

使用してストレージ アカウントを作成する場合、 **Read-access Geo Redundant**レプリケーション オプションをアカウント名のショートカット メニューを開き、そのセカンダリ エンドポイントを表示して選択し、**プロパティ**.

![ストレージのセカンダリ エンドポイント](./media/vs-azure-tools-storage-resources-server-explorer-browse-manage/IC766040.png)

### <a name="to-remove-a-storage-account-from-server-explorer"></a>サーバー エクスプ ローラーからストレージ アカウントを削除するには

サーバー エクスプ ローラーで、アカウント名のショートカット メニューを開くし、選択**削除**します。 

ストレージ アカウントを削除すると、そのアカウントに保存されているキー情報も削除されます。

サーバー エクスプ ローラーからストレージ アカウントを削除するとしても、ストレージ アカウントまたはそれに含まれるすべてのデータに影響しません。 単に、サーバー エクスプ ローラーからの参照を削除します。 ストレージ アカウントを完全に削除するには、使用、 [Azure portal](https://portal.azure.com/)します。

## <a name="next-steps"></a>次の手順

Azure storage サービスを使用する方法の詳細については、次を参照してください。 [、Azure ストレージ サービスにアクセスする](https://msdn.microsoft.com/library/azure/ee405490.aspx)します。
