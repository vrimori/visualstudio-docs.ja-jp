---
title: "チュートリアル : n 層データ アプリケーションの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "n 層アプリケーション, 作成"
  - "n 層アプリケーション, チュートリアル"
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: 48
caps.handback.revision: 48
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# チュートリアル : n 層データ アプリケーションの作成
*n 層*データ アプリケーションとは、データにアクセスするアプリケーションの中でも、複数の論理レイヤー、つまり*層*に分離されるアプリケーションです。  アプリケーション コンポーネントをこのように別個の層に分離すると、アプリケーションの保守容易性とスケーラビリティが向上します。  これは、ソリューション全体を再設計しなくても 1 つの層に適用できる、新しい技術を簡単に導入できるようにすることで実現されます。  n 層アーキテクチャには、プレゼンテーション層、中間層、およびデータ層が存在します。  通常、中間層には、データ アクセス層、ビジネス ロジック層、および認証や検証などの共有コンポーネントが含まれます。  データ層には、リレーショナル データベースが含まれます。  通常、n 層アプリケーションでは、機密情報が中間層のデータ アクセス層に格納され、プレゼンテーション層にアクセスするエンド ユーザーから分離されます。  詳細については、「[n 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)」を参照してください。  
  
 n 層アプリケーションで各層を分離する 1 つの方法は、アプリケーションに組み込む層ごとに別個のプロジェクトを作成することです。  型指定されたデータセットには、生成されたデータセットと `TableAdapter` コードの格納先となるプロジェクトを決定する、`DataSet Project` プロパティが含まれています。  
  
 このチュートリアルでは、**データセット デザイナー**を使用して、別個のクラス ライブラリ プロジェクトにデータセットと `TableAdapter` コードを分離する方法を示します。  データセットと TableAdapter コードを分離したら、データ アクセス層を呼び出す [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) サービスを作成します。  最後に、プレゼンテーション層として Windows フォーム アプリケーションを作成します。  この層は、データ サービスからデータにアクセスします。  
  
 このチュートリアルでは、次の手順を実行します。  
  
-   複数のプロジェクトを含む新しい n 層ソリューションを作成する。  
  
-   この n 層ソリューションに 2 つのクラス ライブラリ プロジェクトを追加する。  
  
-   **データ ソース構成ウィザード**を実行して、型指定されたデータセットを作成する。  
  
-   生成された [TableAdapter](../Topic/TableAdapters.md) とデータセット コードを別々のプロジェクトに分離する。  
  
-   データ アクセス層を呼び出す Windows Communication Foundation \(WCF\) サービスを作成する。  
  
-   このサービスに、データ アクセス層からデータを取得する関数を作成する。  
  
-   プレゼンテーション層として機能する Windows フォーム アプリケーションを作成する。  
  
-   Windows フォーム コントロールを作成し、データ ソースにバインドする。  
  
-   データ テーブルにデータを読み込むコードを記述する。  
  
 ![ビデオへのリンク](~/data-tools/media/playvideo.gif "PlayVideo") このトピックのビデオ版については、「[ビデオ デモ: n 層データ アプリケーションの作成](http://go.microsoft.com/fwlink/?LinkId=115188)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを完了するには、次の条件が必要です。  
  
-   Northwind サンプル データベースにアクセスします。  詳細については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
## n 層ソリューションの作成とデータセットを保持するクラス ライブラリ \(DataEntityTier\) の作成  
 このチュートリアルでは、まず、1 つのソリューションと 2 つのクラス ライブラリ プロジェクトを作成します。  最初のクラス ライブラリは、データセット \(生成した型指定された DataSet クラスと、アプリケーションのデータを保持する DataTable\) を保持します。  このプロジェクトは、アプリケーションのデータ エンティティ層として使用され、通常は中間層に配置されます。  [型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)を使用して初期データセットを作成すると、コードが自動的に 2 つのクラス ライブラリに分離されます。  
  
> [!NOTE]
>  **\[OK\]** をクリックする前に、必ずプロジェクトとソリューションに適切な名前を付けてください。  これにより、チュートリアルの完了が容易になります。  
  
#### n 層ソリューションと DataEntityTier クラス ライブラリを作成するには  
  
1.  **\[ファイル\]** メニューで新しいプロジェクトを作成します。  
  
    > [!NOTE]
    >  **データセット デザイナー**は、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] と C\# のプロジェクトでサポートされています。  新しいプロジェクトはこれらの言語のどちらかで作成してください。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスで、**\[プロジェクトの種類\]** ペインの **\[Windows\]** をクリックします。  
  
3.  **\[クラス ライブラリ\]** テンプレートをクリックします。  
  
4.  プロジェクトに「DataEntityTier」という名前を付けます。  
  
5.  ソリューションに「NTierWalkthrough」という名前を付けます。  
  
6.  **\[OK\]** をクリックします。  
  
     DataEntityTier プロジェクトを含む NTierWalkthrough ソリューションが作成され、**ソリューション エクスプローラー**に追加されます。  
  
## TableAdapter \(DataAccessTier\) を保持するクラス ライブラリの作成  
 DataEntityTier プロジェクトを作成したら、次に、クラス ライブラリ プロジェクトをもう 1 つ作成します。  このプロジェクトは、生成された `TableAdapter` を保持し、アプリケーションの*データ アクセス層*と呼ばれます。  データ アクセス層は、データベースへの接続に必要な情報を格納し、通常、中間層に置かれます。  
  
#### TableAdapter を保持する新しいクラス ライブラリを作成するには  
  
1.  **\[ファイル\]** メニューから、NTierWalkthrough ソリューションに新しいプロジェクトを追加します。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスで、**\[テンプレート\]** ペインの **\[クラス ライブラリ\]** をクリックします。  
  
3.  プロジェクトに「DataAccessTier」という名前を付け、**\[OK\]** をクリックします。  
  
     DataAccessTier プロジェクトが作成され、NTierWalkthrough ソリューションに追加されます。  
  
## データセットの作成  
 次に、型指定されたデータセットを作成します。  型指定されたデータセットは、データセット クラス \(DataTable クラスを含む\) と `TableAdapter` クラスの両方を含む単一のプロジェクトとして作成されます   \(すべてのクラスが 1 つのファイルに生成されます\)。データセットと `TableAdapter` を別個のプロジェクトに分離すると、データセット クラスが別のプロジェクトに移動し、`TableAdapter` クラスは元のプロジェクトに残ります。  このため、最終的に `TableAdapter` が含まれるプロジェクト \(DataAccessTier プロジェクト\) にデータセットを作成します。  データセットは、**データ ソース構成ウィザード**を使用して作成します。  
  
> [!NOTE]
>  接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。  Northwind サンプル データベースの設定方法については、「[方法 : サンプル データベースをインストールする](../data-tools/how-to-install-sample-databases.md)」を参照してください。  
  
#### データセットを作成するには  
  
1.  **ソリューション エクスプローラー**で、\[DataAccessTier\] をクリックします。  
  
2.  **\[データ\]** メニューの **\[データ ソースの表示\]** をクリックします。  
  
3.  **\[データ ソース\]** ウィンドウで、**\[新しいデータ ソースの追加\]** をクリックして**データ ソース構成ウィザード**を起動します。  
  
4.  **\[データ ソースの種類を選択\]** ページで、**\[データベース\]** をクリックし、**\[次へ\]** をクリックします。  
  
5.  **\[データ接続の選択\]** ページで、次のいずれかの操作を行います。  
  
     Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は、これをクリックします。  
  
     または  
  
     **\[新しい接続\]** をクリックして **\[接続の追加\]** ダイアログ ボックスを表示します。  
  
6.  データベースにパスワードが必要な場合は、該当するオプションを選択して重要情報を含め、**\[次へ\]** をクリックします。  
  
    > [!NOTE]
    >  SQL Server に接続するのではなく、ローカル データベース ファイルを選択した場合は、ファイルをプロジェクトに追加するかどうかをたずねるメッセージが表示されます。  **\[はい\]** をクリックして、データベース ファイルをプロジェクトに追加します。  
  
7.  **\[アプリケーション構成ファイルへの接続文字列を保存\]** ページで、**\[次へ\]** をクリックします。  
  
8.  **\[データベース オブジェクトの選択\]** ページの **\[テーブル\]** ノードを展開します。  
  
9. **Customers** テーブルと **Orders** テーブルに該当するチェック ボックスをオンにし、**\[完了\]** をクリックします。  
  
     NorthwindDataSet が DataAccessTier プロジェクトに追加され、**\[データ ソース\]** ウィンドウに表示されます。  
  
## データセットと TableAdapter の分離  
 データセットを作成したら、生成されたデータセット クラスを TableAdapter から分離します。  これを行うには、**"DataSet プロジェクト"** プロパティを、分離されたデータセット クラスを格納するプロジェクトの名前に設定します。  
  
#### データセットと TableAdapter を分離するには  
  
1.  **ソリューション エクスプローラー**で **NorthwindDataSet.xsd** をダブルクリックして、このデータセットを**データセット デザイナー**で開きます。  
  
2.  デザイナーの空の領域をクリックします。  
  
3.  **\[プロパティ\]** ウィンドウで、**\[DataSet プロジェクト\]** ノードを見つけます。  
  
4.  **\[DataSet プロジェクト\]** ボックスの一覧の **\[DataEntityTier\]** をクリックします。  
  
5.  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックします。  
  
 データセットと TableAdapter が、2 つのクラス ライブラリ プロジェクトに分離されます。  最初にデータセット全体 \(DataAccessTier\) を含んでいたプロジェクトには、現在は TableAdapter しか含まれません。  **"DataSet プロジェクト"** プロパティで指定したプロジェクト \(DataEntityTier\) には、型指定されたデータセット \(NorthwindDataSet.Dataset.Designer.vb または NorthwindDataSet.Dataset.Designer.cs\) が含まれます。  
  
> [!NOTE]
>  **"DataSet プロジェクト"** プロパティを設定してデータセットと TableAdapter を分離する場合でも、プロジェクト内の既存のデータセット部分クラスは自動的には移動されません。  既存のデータセット部分クラスは、手動でデータセット プロジェクトに移動する必要があります。  
  
## 新しいサービス アプリケーションの作成  
 このチュートリアルでは WCF サービスを使用してデータ アクセス層にアクセスする方法を説明するので、新しい WCF サービス アプリケーションを作成します。  
  
#### 新しい WCF サービス アプリケーションを作成するには  
  
1.  **\[ファイル\]** メニューから、NTierWalkthrough ソリューションに新しいプロジェクトを追加します。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスで、**\[プロジェクトの種類\]** ペインの **\[WCF\]** をクリックします。  **\[テンプレート\]** ペインの **\[WCF サービス ライブラリ\]** をクリックします。  
  
3.  プロジェクトに「DataService」という名前を付け、**\[OK\]** をクリックします。  
  
     DataService プロジェクトが作成されて NTierWalkthrough ソリューションに追加されます。  
  
## Customers および Orders のデータを返すデータ アクセス層のメソッドの作成  
 データ サービスは、データ アクセス層の 2 つのメソッド \(GetCustomers および GetOrders\) を呼び出す必要があります。  これらのメソッドは、Northwind の Customers テーブルと Orders テーブルを返します。  GetCustomers メソッドと GetOrders メソッドは、DataAccessTier プロジェクトに作成します。  
  
#### Customers テーブルを返すメソッドをデータ アクセス層に作成するには  
  
1.  **ソリューション エクスプローラー**で NorthwindDataset.xsd をダブルクリックして、データセットを[型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)で開きます。  
  
2.  \[CustomersTableAdapter\] を右クリックし、**\[クエリの追加\]** をクリックして [TableAdapter クエリの構成ウィザード](../data-tools/editing-tableadapters.md)を開きます。  
  
3.  **\[コマンドの種類を選択します\]** ページで、**\[SQL ステートメントを使用する\]** の既定値を受け入れ、**\[次へ\]** をクリックします。  
  
4.  **\[クエリの種類の選択\]** ページで、**\[複数行を返す SELECT\]** の既定値を受け入れ、**\[次へ\]** をクリックします。  
  
5.  **\[SQL SELECT ステートメントの指定\]** ページで、既定のクエリを受け入れ、**\[次へ\]** をクリックします。  
  
6.  **\[生成するメソッドの選択\]** ページで、**\[DataTable を返す\]** セクションの **\[メソッド名\]** に「GetCustomers」と入力します。  
  
7.  **\[完了\]** をクリックします。  
  
#### Orders テーブルを返すメソッドをデータ アクセス層に作成するには  
  
1.  \[OrdersTableAdapter\] を右クリックし、**\[クエリの追加\]** をクリックします。  
  
2.  **\[コマンドの種類を選択します\]** ページで、**\[SQL ステートメントを使用する\]** の既定値を受け入れ、**\[次へ\]** をクリックします。  
  
3.  **\[クエリの種類の選択\]** ページで、**\[複数行を返す SELECT\]** の既定値を受け入れ、**\[次へ\]** をクリックします。  
  
4.  **\[SQL SELECT ステートメントの指定\]** ページで、既定のクエリを受け入れ、**\[次へ\]** をクリックします。  
  
5.  **\[生成するメソッドの選択\]** ページで、**\[DataTable を返す\]** セクションの **\[メソッド名\]** に「GetOrders」と入力します。  
  
6.  **\[完了\]** をクリックします。  
  
7.  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックします。  
  
## データ サービスへの、データ エンティティ層およびデータ アクセス層への参照の追加  
 データ サービスはデータセットと TableAdapter の情報を必要とするため、DataEntityTier プロジェクトおよび DataAccessTier プロジェクトへの参照を追加します。  
  
#### データ サービスに参照を追加するには  
  
1.  **ソリューション エクスプローラー**で、\[DataService\] を右クリックし、**\[参照の追加\]** をクリックします。  
  
2.  **\[参照の追加\]** ダイアログ ボックスの **\[プロジェクト\]** タブをクリックします。  
  
3.  **\[DataAccessTier\]** プロジェクトと **\[DataEntityTier\]** プロジェクトの両方を選択します。  
  
4.  **\[OK\]** をクリックします。  
  
## データ アクセス層の GetCustomers メソッドおよび GetOrders メソッドを呼び出す関数のサービスへの追加  
 これで、データを返すメソッドをデータ アクセス層に含めることができました。次に、データ サービスにメソッドを作成して、データ アクセス層のメソッドを呼び出します。  
  
> [!NOTE]
>  C\# プロジェクトの場合は、次のコードをコンパイルするために `System.Data.DataSetExtensions` アセンブリへの参照を追加する必要があります。  
  
#### データ サービスに GetCustomers 関数と GetOrders 関数を作成するには  
  
1.  **DataService** プロジェクトで、IService1.vb または IService1.cs をダブルクリックします。  
  
2.  **"Add your service operations here"** というコメントの下に、次のコードを追加します。  
  
    ```vb#  
    <OperationContract()> _  
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable  
  
    <OperationContract()> _  
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable  
    ```  
  
    ```c#  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();  
  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();  
  
    ```  
  
3.  DataService プロジェクトで、Service1.vb または Service1.cs をダブルクリックします。  
  
4.  Service1 クラスに次のコードを追加します。  
  
    ```vb#  
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers  
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter  
        Return CustomersTableAdapter1.GetCustomers()  
    End Function  
  
    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders  
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter  
        Return OrdersTableAdapter1.GetOrders()  
    End Function  
    ```  
  
    ```c#  
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
  
5.  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックします。  
  
## データ サービスのデータを表示するプレゼンテーション層の作成  
 これで、データ アクセス層を呼び出すメソッドを持つデータ サービスをソリューションに含めることができました。次に、データ サービスを呼び出してデータをユーザーに表示する別のプロジェクトを作成します。  このチュートリアルでは、Windows フォーム アプリケーションを作成します。これは n 層アプリケーションのプレゼンテーション層です。  
  
#### プレゼンテーション層プロジェクトを作成するには  
  
1.  **\[ファイル\]** メニューから、NTierWalkthrough ソリューションに新しいプロジェクトを追加します。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスで、**\[プロジェクトの種類\]** ペインの **\[Windows\]** をクリックします。  **\[テンプレート\]** ペインの **\[Windows フォーム アプリケーション\]** をクリックします。  
  
3.  プロジェクトに「PresentationTier」という名前を付け、**\[OK\]** をクリックします。  
  
4.  PresentationTier プロジェクトが作成され、NTierWalkthrough ソリューションに追加されます。  
  
## スタートアップ プロジェクトとしての PresentationTier プロジェクトの設定  
 プレゼンテーション層は、データを提示して対話するために使用する実際のクライアント アプリケーションです。このため、PresentationTier プロジェクトをスタートアップ プロジェクトとして設定する必要があります。  
  
#### 新しいプレゼンテーション層プロジェクトをスタートアップ プロジェクトとして設定するには  
  
-   **ソリューション エクスプローラー**で、**\[PresentationTier\]** を右クリックし、**\[スタートアップ プロジェクトに設定\]** をクリックします。  
  
## プレゼンテーション層への参照の追加  
 クライアント アプリケーションである PresentationTier には、サービスのメソッドにアクセスできるように、データ サービスへのサービス参照が必要です。  また、WCF サービスによる型の共有を有効にするために、データセットへの参照も必要です。  データセット部分クラスに追加したコードは、データ サービスを介した型の共有を有効にするまで、プレゼンテーション層で使用することはできません。  通常は、データ テーブルの行と列の変更イベントに検証などのコードを追加するため、クライアントからこのコードにアクセスすることが必要になります。  
  
#### プレゼンテーション層に参照を追加するには  
  
1.  **ソリューション エクスプローラー**で、\[PresentationTier\] を右クリックし、**\[参照の追加\]** をクリックします。  
  
2.  **\[参照の追加\]** ダイアログ ボックスの **\[プロジェクト\]** タブをクリックします。  
  
3.  **\[DataEntityTier\]** を選択し、**\[OK\]** をクリックします。  
  
#### プレゼンテーション層にサービス参照を追加するには  
  
1.  **ソリューション エクスプローラー**で、\[PresentationTier\] を右クリックし、**\[サービス参照の追加\]** をクリックします。  
  
2.  **\[サービス参照の追加\]** ダイアログ ボックスで **\[探索\]** をクリックします。  
  
3.  **\[Service1\]** を選択し、**\[OK\]** をクリックします。  
  
    > [!NOTE]
    >  現在のコンピューターに複数のサービスがある場合は、このチュートリアルで以前に作成したサービス \(GetCustomers メソッドおよび GetOrders メソッドを含むサービス\) を選択します。  
  
## フォームへの DataGridView の追加とデータ サービスから返されたデータの表示  
 データ サービスへのサービス参照を追加すると、サービスによって返されたデータが **\[データ ソース\]** ウィンドウに自動的に読み込まれます。  
  
#### フォームに 2 つのデータ バインド DataGridView を追加するには  
  
1.  **ソリューション エクスプローラー**で、PresentationTier プロジェクトを選択します。  
  
2.  **\[データ ソース\]** ウィンドウの **\[NorthwindDataSet\]** を展開し、**\[Customers\]** ノードを見つけます。  
  
3.  **\[Customers\]** ノードを Form1 にドラッグします。  
  
4.  **\[データ ソース\]** ウィンドウの **\[Customers\]** ノードを展開し、関連する **\[Orders\]** ノード \(**\[Customers\]** ノードに入れ子になっている **\[Orders\]** ノード\) を見つけます。  
  
5.  関連する **\[Orders\]** ノードを Form1 にドラッグします。  
  
6.  フォームの空の領域をダブルクリックして、`Form1_Load` イベント ハンドラーを作成します。  
  
7.  `Form1_Load` イベント ハンドラーに次のコードを追加します。  
  
    ```vb#  
    Dim DataSvc As New ServiceReference1.Service1Client  
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)  
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)  
    ```  
  
    ```c#  
    ServiceReference1.Service1Client DataSvc =   
        new ServiceReference1.Service1Client();  
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());  
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());  
  
    ```  
  
## サービスで許可されるメッセージの最大サイズの増加  
 サービスは Customers テーブルと Orders テーブルからデータを返すため、maxReceivedMessageSize の既定値ではデータを保持するのに十分ではなく、この値を大きくする必要があります。  このチュートリアルでは、値を 6553600 に変更します。  クライアントで値を変更すると、サービス参照が自動的に更新されます。  
  
> [!NOTE]
>  既定のサイズが低く設定されているのは、サービス拒否 \(DoS\) 攻撃を受けるリスクを低減するためです。  詳細については、「<xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>」を参照してください。  
  
#### maxReceivedMessageSize 値を増やすには  
  
1.  **ソリューション エクスプローラー**で、PresentationTier プロジェクトの app.config ファイルをダブルクリックします。  
  
2.  **maxReceivedMessage** サイズ属性を見つけ、値を「`6553600`」に変更します。  
  
## アプリケーションのテスト  
 アプリケーションを実行します。  データがデータ サービスから取得され、フォームに表示されます。  
  
#### アプリケーションをテストするには  
  
1.  F5 キーを押します。  
  
2.  Customers テーブルと Orders テーブルのデータがデータ サービスから取得され、フォームに表示されます。  
  
## 次の手順  
 Windows ベース アプリケーションに関連データを保存した後で、アプリケーションの要件によってはさらに操作を追加する必要があります。  たとえば、このアプリケーションに対して次のような拡張を行うことができます。  
  
-   データセットへの検証の追加。  詳細については、「[チュートリアル : n 層データ アプリケーションへの検証の追加](../Topic/Walkthrough:%20Adding%20Validation%20to%20an%20N-Tier%20Data%20Application.md)」を参照してください。  
  
-   サービスへの、データを更新してデータベースに戻す追加メソッドの追加。  
  
## 参照  
 [n 層アプリケーションでのデータセットの操作](../data-tools/work-with-datasets-in-n-tier-applications.md)   
 [階層更新](../data-tools/hierarchical-update.md)   
 [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)