---
title: 'チュートリアル : n 層データ アプリケーションの作成'
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 71c1c8dbaf34613d07ce29fa3f5e08d8e9c6961f
ms.sourcegitcommit: 81e9d90843ead658bc73b30c869f25921d99e116
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2018
ms.locfileid: "52305703"
---
# <a name="walkthrough-create-an-n-tier-data-application"></a>チュートリアル: n 層データ アプリケーションを作成します。
*n 層*データ アプリケーションとは、データにアクセスするアプリケーションの中でも、複数の論理レイヤー、つまり*層*に分離されるアプリケーションです。 アプリケーション コンポーネントをこのように別個の層に分離すると、アプリケーションの保守容易性とスケーラビリティが向上します。 これは、ソリューション全体を再設計しなくても 1 つの層に適用できる、新しい技術を簡単に導入できるようにすることで実現されます。 n 層アーキテクチャには、プレゼンテーション層、中間層、およびデータ層が存在します。 通常、中間層には、データ アクセス層、ビジネス ロジック層、および認証や検証などの共有コンポーネントが含まれます。 データ層には、リレーショナル データベースが含まれます。 通常、n 層アプリケーションでは、機密情報が中間層のデータ アクセス層に格納され、プレゼンテーション層にアクセスするエンド ユーザーから分離されます。 詳細については、次を参照してください。 [N 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)します。

n 層アプリケーションで各層を分離する 1 つの方法は、アプリケーションに組み込む層ごとに別個のプロジェクトを作成することです。 型指定されたデータセットには、生成されたデータセットと `DataSet Project` コードの格納先となるプロジェクトを決定する、`TableAdapter` プロパティが含まれています。

このチュートリアルでは、**データセット デザイナー**を使用して、別個のクラス ライブラリ プロジェクトにデータセットと `TableAdapter` コードを分離する方法を示します。 作成したデータセットと TableAdapter コードを分離する、 [Windows Communication Foundation サービスと Visual Studio での WCF Data Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)データ アクセス層を呼び出すサービス。 最後に、プレゼンテーション層としての Windows フォーム アプリケーションを作成します。 この層は、データ サービスからデータにアクセスします。

このチュートリアルでは、次の手順を実行します。

-   複数のプロジェクトを含む新しい n 層ソリューションを作成します。

-   この n 層ソリューションに 2 つのクラス ライブラリ プロジェクトを追加する。

-   **データ ソース構成ウィザード**を実行して、型指定されたデータセットを作成する。

-   生成された分離[Tableadapter](create-and-configure-tableadapters.md)と別々 のプロジェクトにデータセット コード。

-   データ アクセス層を呼び出す Windows Communication Foundation (WCF) サービスを作成する。

-   このサービスに、データ アクセス層からデータを取得する関数を作成する。

-   プレゼンテーション層として機能する Windows フォーム アプリケーションを作成する。

-   Windows フォーム コントロールを作成し、データ ソースにバインドする。

-   データ テーブルにデータを読み込むコードを記述する。

![ビデオへのリンク](../data-tools/media/playvideo.gif)このトピックのビデオ版について、次を参照してください。 [Video How to: n 層データ アプリケーションを作成する](http://go.microsoft.com/fwlink/?LinkId=115188)します。

## <a name="prerequisites"></a>必須コンポーネント
このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。

1. SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server Express のダウンロード ページ](https://www.microsoft.com/sql-server/sql-server-editions-express)、または、 **Visual Studio インストーラー**します。 **Visual Studio インストーラー**の一部として SQL Server Express LocalDB をインストールすることができます、 **.NET デスクトップ開発**ワークロード、または個々 のコンポーネントとして。

2. 次の手順に従って、Northwind サンプル データベースをインストールします。

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウ。 (**SQL Server オブジェクト エクスプ ローラー**がの一部としてインストールされている、**データ ストレージと処理**Visual Studio インストーラーにワークロード)。展開、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリ**します。

       クエリ エディター ウィンドウが開きます。

    2. コピー、 [Northwind Transact SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトでは、最初から、Northwind データベースを作成し、データを設定します。

    3. T-SQL スクリプトをクエリ エディターに貼り付けて選択し、 **Execute**ボタンをクリックします。

       しばらくすると、クエリの実行が完了し、Northwind データベースを作成します。

## <a name="create-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>データセット (DataEntityTier) を保持する n 層ソリューションとクラス ライブラリを作成します。
 このチュートリアルでは、まず、1 つのソリューションと 2 つのクラス ライブラリ プロジェクトを作成します。 最初のクラス ライブラリは、データセットを保持 (生成された型指定された`DataSet`クラスと、アプリケーションのデータを保持する Datatable)。 このプロジェクトは、アプリケーションのデータ エンティティ層として使用され、通常は中間層に配置されます。 データセットは、初期データセットを作成し、2 つのクラス ライブラリにコードを自動的に分割します。

> [!NOTE]
> **[OK]** をクリックする前に、必ずプロジェクトとソリューションに適切な名前を付けてください。 これにより、チュートリアルの完了が容易になります。

### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>n 層ソリューションと DataEntityTier クラス ライブラリを作成するには

1. Visual Studio での**ファイル**メニューの **新規** > **プロジェクト**します。

2. いずれかを展開**Visual c#** または**Visual Basic**左側のウィンドウでを選択し、 **Windows デスクトップ**します。

3. 中央のペインで選択、**クラス ライブラリ**プロジェクトの種類。

4. プロジェクトに「**DataEntityTier**」という名前を付けます。

5. ソリューションの名前を**NTierWalkthrough**を選び、 **OK**します。

     DataEntityTier プロジェクトを含む NTierWalkthrough ソリューションが作成され、**ソリューション エクスプローラー**に追加されます。

## <a name="create-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Tableadapter (DataAccessTier) を保持するために、クラス ライブラリを作成します。
 DataEntityTier プロジェクトを作成したら、次に、クラス ライブラリ プロジェクトをもう 1 つ作成します。 このプロジェクトが生成された Tableadapter を保持しと呼ばれますが、*データ アクセス層*アプリケーション。 データ アクセス層は、データベースへの接続に必要な情報を格納し、通常、中間層に置かれます。

### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>Tableadapter の別のクラス ライブラリを作成するには

1. ソリューションを右クリックして**ソリューション エクスプ ローラー**選択**追加** > **新しいプロジェクト**します。

2. **新しいプロジェクト** ダイアログ ボックスで、選択の中央のペインで**クラス ライブラリ**します。

3. プロジェクトに名前を**DataAccessTier**選択**OK**します。

     DataAccessTier プロジェクトが作成され、NTierWalkthrough ソリューションに追加されます。

## <a name="create-the-dataset"></a>データセットを作成します。
 次に、型指定されたデータセットを作成します。 Dataset クラスで型指定されたデータセットが作成されます (含む`DataTables`クラス) と`TableAdapter`1 つのプロジェクト内のクラス。 (すべてのクラスが 1 つのファイルに生成されます)。まま、その他のプロジェクトに移動されたデータセット クラスが、データセットと TableAdapters を別々 のプロジェクトに分離する場合、`TableAdapter`元のプロジェクト内のクラス。 そのため、Tableadapter (DataAccessTier プロジェクト) を含む最終的にプロジェクトで、データセットを作成します。 使用して、データセットを作成して、**データ ソース構成ウィザード**します。

> [!NOTE]
> 接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。 Northwind サンプル データベースを設定する方法については、次を参照してください。[方法: サンプル データベースをインストール](../data-tools/installing-database-systems-tools-and-samples.md)します。

### <a name="to-create-the-dataset"></a>データセットを作成するには

1. 選択、 **DataAccessTier**で**ソリューション エクスプ ローラー**します。

2. **データ**メニューの  **データ ソースの**します。

   **[データ ソース]** ウィンドウが開きます。

3. **[データ ソース]** ウィンドウで、**[新しいデータ ソースの追加]** をクリックして**データ ソース構成ウィザード**を起動します。

4. **データ ソースの種類を選択** ページで、**データベース**し、**次**します。

5. **[データ接続の選択]** ページで、次のいずれかの操作を行います。

     Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。

     - または -

     選択**新しい接続**を開く、**接続の追加** ダイアログ ボックス。

6. データベースは、パスワードを必要とする場合、機密データを含めるし、オプションを選択**次**します。

    > [!NOTE]
    > SQL Server に接続するのではなく、ローカル データベース ファイルを選択した場合は、ファイルをプロジェクトに追加するかどうかをたずねるメッセージが表示されます。 選択**はい**データベース ファイルをプロジェクトに追加します。

7. 選択**次**上、**アプリケーション構成ファイルへの接続文字列を保存**ページ。

8. **[データベース オブジェクトの選択]** ページの **[テーブル]** ノードを展開します。

9. チェック ボックスをオン、**顧客**と**注文**テーブル、および選択**完了**します。

     NorthwindDataSet が DataAccessTier プロジェクトに追加され、**[データ ソース]** ウィンドウに表示されます。

## <a name="separate-the-tableadapters-from-the-dataset"></a>データセットから、Tableadapter を分離します。
 データセットを作成したら、生成されたデータセット クラスを TableAdapter から分離します。 これを行うには、**[DataSet プロジェクト]** プロパティを、分離されたデータセット クラスを格納するプロジェクトの名前に設定します。

### <a name="to-separate-the-tableadapters-from-the-dataset"></a>データセットと TableAdapter を分離するには

1. **ソリューション エクスプローラー**で **NorthwindDataSet.xsd** をダブルクリックし、**データセット デザイナー**でデータセットを開きます。

2. デザイナーの空の領域を選択します。

3. **[プロパティ]** ウィンドウで **[DataSet プロジェクト]** ノードを見つけます。

4. **DataSet プロジェクト**一覧で、 **DataEntityTier**します。

5. **[ビルド]** メニューの **[ソリューションのビルド]** を選択します。

   データセットと TableAdapter が、2 つのクラス ライブラリ プロジェクトに分離されます。 データセット全体を含んでいたプロジェクト (`DataAccessTier`) には Tableadapter しか含まれています。 指定したプロジェクト、 **DataSet プロジェクト**プロパティ (`DataEntityTier`)、型指定されたデータセットが含まれています: *NorthwindDataSet.Dataset.Designer.vb* (または*NorthwindDataSet.Dataset.Designer.cs*)。

> [!NOTE]
> **[DataSet プロジェクト]** プロパティを設定してデータセットと TableAdapter を分離する場合でも、プロジェクト内の既存のデータセット部分クラスは自動的には移動されません。 既存のデータセット部分クラスは、手動でデータセット プロジェクトに移動する必要があります。

## <a name="create-a-new-service-application"></a>新しいサービス アプリケーションを作成します。
このチュートリアルでは、WCF サービスを使用して、データ アクセス層へのアクセス、それでは、新しい WCF サービス アプリケーションを作成する方法を示します。

### <a name="to-create-a-new-wcf-service-application"></a>新しい WCF サービス アプリケーションを作成するには

1. ソリューションを右クリックして**ソリューション エクスプ ローラー**選択**追加** > **新しいプロジェクト**します。

2. **新しいプロジェクト** ダイアログ ボックスで、選択の左側のウィンドウで**WCF**します。 中央のペインで選択**WCF サービス ライブラリ**します。

3. プロジェクトに名前を**DataService**選択**OK**。

     DataService プロジェクトが作成されて NTierWalkthrough ソリューションに追加されます。

## <a name="create-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>顧客と注文データを返すデータ アクセス層のメソッドを作成します。
 データ サービスが、データ アクセス層に 2 つのメソッドを呼び出すには:`GetCustomers`と`GetOrders`します。 これらのメソッドは、Northwind を返す`Customers`と`Orders`テーブル。 作成、`GetCustomers`と`GetOrders`メソッド、`DataAccessTier`プロジェクト。

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Customers テーブルを返すメソッドをデータ アクセス層に作成するには

1. **ソリューション エクスプ ローラー**、ダブルクリックして**NorthwindDataset.xsd**データセットを開きます。

2. 右クリック**CustomersTableAdapter**クリック**クエリの追加**します。

3. **[コマンドの種類を選択します]** ページで、**[SQL ステートメントを使用する]** の既定値を受け入れ、**[次へ]** をクリックします。

4. **[クエリの種類の選択]** ページで、**[複数行を返す SELECT]** の既定値を受け入れ、**[次へ]** をクリックします。

5. **[SQL SELECT ステートメントの指定]** ページで、既定のクエリを受け入れ、**[次へ]** をクリックします。

6. **[生成するメソッドの選択]** ページで、**[DataTable を返す]** セクションの **[メソッド名]** に「**GetCustomers**」と入力します。

7. **[完了]** をクリックします。

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Orders テーブルを返すメソッドをデータ アクセス層に作成するには

1. **[OrdersTableAdapter]** を右クリックし、**[クエリの追加]** をクリックします。

2. **[コマンドの種類を選択します]** ページで、**[SQL ステートメントを使用する]** の既定値を受け入れ、**[次へ]** をクリックします。

3. **[クエリの種類の選択]** ページで、**[複数行を返す SELECT]** の既定値を受け入れ、**[次へ]** をクリックします。

4. **[SQL SELECT ステートメントの指定]** ページで、既定のクエリを受け入れ、**[次へ]** をクリックします。

5. **[生成するメソッドの選択]** ページで、**[DataTable を返す]** セクションの **[メソッド名]** に「**GetOrders**」と入力します。

6. **[完了]** をクリックします。

7. **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。

## <a name="add-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>データ サービスにデータ エンティティへの参照およびデータ アクセス層を追加します。
 データ サービスはデータセットと TableAdapter の情報を必要とするため、**DataEntityTier** プロジェクトおよび **DataAccessTier** プロジェクトへの参照を追加します。

### <a name="to-add-references-to-the-data-service"></a>データ サービスに参照を追加するには

1. **ソリューション エクスプローラー**で、**[DataService]** を右クリックし、**[参照の追加]** をクリックします。

2. **[参照の追加]** ダイアログ ボックスの **[プロジェクト]** タブをクリックします。

3. **[DataAccessTier]** プロジェクトと **[DataEntityTier]** プロジェクトの両方を選択します。

4. **[OK]** をクリックします。

## <a name="add-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>関数をデータ アクセス層の getcustomers メソッドおよび GetOrders メソッドを呼び出すサービスの追加します。
 これで、データを返すメソッドをデータ アクセス層に含めることができました。次に、データ サービスにメソッドを作成して、データ アクセス層のメソッドを呼び出します。

> [!NOTE]
> C# プロジェクトの場合は、次のコードをコンパイルするために `System.Data.DataSetExtensions` アセンブリへの参照を追加する必要があります。

### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>データ サービスに GetCustomers 関数と GetOrders 関数を作成するには

1. **DataService** プロジェクトで、**IService1.vb** または **IService1.cs** をダブルクリックします。

2. **[Add your service operations here]** というコメントの下に、次のコードを追加します。

    ```vb
    <OperationContract()> _
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable

    <OperationContract()> _
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable
    ```

    ```csharp
    [OperationContract]
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();

    [OperationContract]
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();
    ```

3. DataService プロジェクトで、**Service1.vb** または **Service1.cs** をダブルクリックします。

4. **Service1** クラスに次のコードを追加します。

    ```vb
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
        Return CustomersTableAdapter1.GetCustomers()
    End Function

    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
        Return OrdersTableAdapter1.GetOrders()
    End Function
    ```

    ```csharp
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
             CustomersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();
        return CustomersTableAdapter1.GetCustomers();
    }
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
             OrdersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();
        return OrdersTableAdapter1.GetOrders();
    }
    ```

5. **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。

## <a name="create-a-presentation-tier-to-display-data-from-the-data-service"></a>データ サービスからデータを表示するプレゼンテーション層を作成します。
 これで、ソリューションには、データ サービスであり、メソッド、データにどの呼び出しは、層にアクセス、データ サービスを呼び出す別のプロジェクトを作成し、データをユーザーに提供が含まれています。 このチュートリアルでは、Windows フォーム アプリケーションを作成します。これは n 層アプリケーションのプレゼンテーション層です。

### <a name="to-create-the-presentation-tier-project"></a>プレゼンテーション層プロジェクトを作成するには

1. ソリューションを右クリックして**ソリューション エクスプ ローラー**選択**追加** > **新しいプロジェクト**します。

2. **新しいプロジェクト** ダイアログ ボックスで、選択の左側のウィンドウで**Windows デスクトップ**します。 中央のペインで選択**Windows フォーム アプリ**します。

3. プロジェクトに「**PresentationTier**」という名前を付け、**[OK]** をクリックします。

    PresentationTier プロジェクトが作成され、NTierWalkthrough ソリューションに追加されます。

## <a name="set-the-presentationtier-project-as-the-startup-project"></a>PresentationTier プロジェクトをスタートアップ プロジェクトとして設定します。
設定、 **PresentationTier**プロジェクト、ソリューションのスタートアップ プロジェクトを提示し、そのデータにアクセスする実際のクライアント アプリケーションであります。

### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>新しいプレゼンテーション層プロジェクトをスタートアップ プロジェクトとして設定するには

-   **ソリューション エクスプローラー**で、**[PresentationTier]** を右クリックし、**[スタートアップ プロジェクトに設定]** をクリックします。

## <a name="add-references-to-the-presentation-tier"></a>プレゼンテーション層への参照を追加します。
 クライアント アプリケーションである PresentationTier には、サービスのメソッドにアクセスできるように、データ サービスへのサービス参照が必要です。 また、WCF サービスによる型の共有を有効にするために、データセットへの参照も必要です。 型のデータ サービスを介した共有を有効にするまでは、データセット部分クラスに追加したコードは、プレゼンテーション層を使用できません。 通常、行と列の変更をデータ テーブルのイベントに検証コードなどのコードを追加するためには、クライアントからこのコードにアクセスしますが高くなります。

### <a name="to-add-a-reference-to-the-presentation-tier"></a>プレゼンテーション層に参照を追加するには

1. **ソリューション エクスプ ローラー**、右クリック**PresentationTier**選択と**参照の追加**します。

2. **参照の追加**ダイアログ ボックスで、**プロジェクト**タブ。

3. 選択**DataEntityTier**選択**OK**します。

### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>プレゼンテーション層にサービス参照を追加するには

1. **ソリューション エクスプ ローラー**、右クリック**PresentationTier**選択**サービス参照の追加**します。

2. **サービス参照の追加**ダイアログ ボックスで、 **Discover**します。

3. 選択**Service1**選択**OK**します。

    > [!NOTE]
    > 現在のコンピューターに複数のサービスがあれば、このチュートリアルで以前に作成したサービスを選択します。 (含まれているサービス、`GetCustomers`と`GetOrders`メソッド)。

## <a name="add-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>データ サービスによって返されるデータを表示するフォームに Datagridview を追加します。
 データ サービスへのサービス参照を追加すると、サービスによって返されたデータが **[データ ソース]** ウィンドウに自動的に読み込まれます。

### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>フォームに 2 つのデータ バインド DataGridView を追加するには

1. **ソリューション エクスプローラー**で、**PresentationTier** プロジェクトを選択します。

2. **[データ ソース]** ウィンドウの **[NorthwindDataSet]** を展開し、**[Customers]** ノードを見つけます。

3. **[Customers]** ノードを Form1 にドラッグします。

4. **[データ ソース]** ウィンドウの **[Customers]** ノードを展開し、関連する **[Orders]** ノード (**[Customers]** ノードに入れ子になっている **[Orders]** ノード) を見つけます。

5. 関連する **[Orders]** ノードを Form1 にドラッグします。

6. フォームの空の領域をダブルクリックして、`Form1_Load` イベント ハンドラーを作成します。

7. `Form1_Load` イベント ハンドラーに次のコードを追加します。

    ```vb
    Dim DataSvc As New ServiceReference1.Service1Client
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)
    ```

    ```csharp
    ServiceReference1.Service1Client DataSvc =
        new ServiceReference1.Service1Client();
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());
    ```

## <a name="increase-the-maximum-message-size-allowed-by-the-service"></a>サービスで許可されている最大メッセージ サイズを増やす
既定値`maxReceivedMessageSize`から取得されたデータを保持するために十分な大きさでない、`Customers`と`Orders`テーブル。 次の手順では、値を 6553600 が増加します。 サービス参照を自動的に更新すると、クライアントで値を変更するとします。

> [!NOTE]
> 既定のサイズが低く設定されているのは、サービス拒否 (DoS) 攻撃を受けるリスクを低減するためです。 詳細については、「<xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>」を参照してください。

### <a name="to-increase-the-maxreceivedmessagesize-value"></a>maxReceivedMessageSize 値を増やすには

1. **ソリューション エクスプローラー**で、**PresentationTier** プロジェクトの **app.config** ファイルをダブルクリックします。

2. **maxReceivedMessage** サイズ属性を見つけ、値を「`6553600`」に変更します。

## <a name="test-the-application"></a>アプリケーションをテストする
**F5** キーを押してアプリケーションを実行します。 データ、`Customers`と`Orders`テーブルがデータ サービスから取得され、フォームに表示します。

## <a name="next-steps"></a>次の手順
 Windows ベース アプリケーションに関連データを保存した後で、アプリケーションの要件によってはさらに操作を追加する必要があります。 たとえば、このアプリケーションに対して次のような拡張を行うことができます。

-   データセットへの検証の追加。

-   サービスへの、データを更新してデータベースに戻す追加メソッドの追加。

## <a name="see-also"></a>関連項目

- [n 層アプリケーションでのデータセットの操作](../data-tools/work-with-datasets-in-n-tier-applications.md)
- [階層更新](../data-tools/hierarchical-update.md)
- [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)