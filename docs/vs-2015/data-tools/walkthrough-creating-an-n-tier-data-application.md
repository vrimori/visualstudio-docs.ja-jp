---
title: 'チュートリアル: N 層データ アプリケーションの作成 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: 51
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 37876502a464e263ebd6803216b29bd62b65af5c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49890180"
---
# <a name="walkthrough-creating-an-n-tier-data-application"></a>チュートリアル : n 層データ アプリケーションの作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
N-レベル * データ アプリケーションは、データにアクセスし、複数の論理レイヤーに分割されているアプリケーションまたは*層*します。 アプリケーション コンポーネントをこのように別個の層に分離すると、アプリケーションの保守容易性とスケーラビリティが向上します。 これは、ソリューション全体を再設計しなくても 1 つの層に適用できる、新しい技術を簡単に導入できるようにすることで実現されます。 n 層アーキテクチャには、プレゼンテーション層、中間層、およびデータ層が存在します。 通常、中間層には、データ アクセス層、ビジネス ロジック層、および認証や検証などの共有コンポーネントが含まれます。 データ層には、リレーショナル データベースが含まれます。 通常、n 層アプリケーションでは、機密情報が中間層のデータ アクセス層に格納され、プレゼンテーション層にアクセスするエンド ユーザーから分離されます。 詳細については、次を参照してください。 [N 層データ アプリケーションの概要](../data-tools/n-tier-data-applications-overview.md)します。  
  
 n 層アプリケーションで各層を分離する 1 つの方法は、アプリケーションに組み込む層ごとに別個のプロジェクトを作成することです。 型指定されたデータセットには、生成されたデータセットと `DataSet Project` コードの格納先となるプロジェクトを決定する、`TableAdapter` プロパティが含まれています。  
  
 このチュートリアルのデータセットを分割する方法について説明し、`TableAdapter`を使用して別個のクラス ライブラリ プロジェクトにコードを**データセット デザイナー**。 作成後、データセットと TableAdapter コードを分離する、 [Windows Communication Foundation サービスと Visual Studio での WCF Data Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)データ アクセス層を呼び出すサービス。 最後に、プレゼンテーション層として Windows フォーム アプリケーションを作成します。 この層は、データ サービスからデータにアクセスします。  
  
 このチュートリアルでは、次の手順を実行します。  
  
- 複数のプロジェクトを含む新しい n 層ソリューションを作成する。  
  
- この n 層ソリューションに 2 つのクラス ライブラリ プロジェクトを追加する。  
  
- 使用して型指定されたデータセットを作成、**データ ソース構成ウィザード**します。  
  
- 生成された分離[Tableadapter](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)と別々 のプロジェクトにデータセット コード。  
  
- データ アクセス層を呼び出す Windows Communication Foundation (WCF) サービスを作成する。  
  
- このサービスに、データ アクセス層からデータを取得する関数を作成する。  
  
- プレゼンテーション層として機能する Windows フォーム アプリケーションを作成する。  
  
- Windows フォーム コントロールを作成し、データ ソースにバインドする。  
  
- データ テーブルにデータを読み込むコードを記述する。  
  
  ![ビデオへのリンク](../data-tools/media/playvideo.gif "PlayVideo")このトピックのビデオ版について、次を参照してください。 [Video How to: N 層データ アプリケーションの作成](http://go.microsoft.com/fwlink/?LinkId=115188)です。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するには、次の条件が必要です。  
  
-   Northwind サンプル データベースにアクセスします。 詳細については、次を参照してください。[方法: サンプル データベースをインストール](../data-tools/how-to-install-sample-databases.md)します。  
  
## <a name="creating-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>n 層ソリューションの作成とデータセットを保持するクラス ライブラリ (DataEntityTier) の作成  
 このチュートリアルでは、まず、1 つのソリューションと 2 つのクラス ライブラリ プロジェクトを作成します。 最初のクラス ライブラリは、データセット (生成した型指定された DataSet クラスと、アプリケーションのデータを保持する DataTable) を保持します。 このプロジェクトは、アプリケーションのデータ エンティティ層として使用され、通常は中間層に配置されます。 [の作成と型指定されたデータセットの編集](../data-tools/creating-and-editing-typed-datasets.md)初期データセットを作成し、2 つのクラス ライブラリに自動的にコードを分離するために使用します。  
  
> [!NOTE]
>  クリックする前に、プロジェクトとソリューションを正しく名前を必ず**OK**します。 これにより、チュートリアルの完了が容易になります。  
  
#### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>n 層ソリューションと DataEntityTier クラス ライブラリを作成するには  
  
1.  **ファイル**] メニューの [新しいプロジェクトを作成します。  
  
    > [!NOTE]
    >  **データセット デザイナー**ではサポートされて[!INCLUDE[vbprvb](../includes/vbprvb-md.md)]と c# プロジェクト。 新しいプロジェクトはこれらの言語のどちらかで作成してください。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、**プロジェクトの種類**ウィンドウで、をクリックして**Windows**します。  
  
3.  をクリックして、**クラス ライブラリ**テンプレート。  
  
4.  プロジェクトに名前を**DataEntityTier**します。  
  
5.  ソリューションの名前を**NTierWalkthrough**します。  
  
6.  **[OK]** をクリックします。  
  
     DataEntityTier プロジェクトを含む NTierWalkthrough ソリューションが作成されに追加**ソリューション エクスプ ローラー**します。  
  
## <a name="creating-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>TableAdapter (DataAccessTier) を保持するクラス ライブラリの作成  
 DataEntityTier プロジェクトを作成したら、次に、クラス ライブラリ プロジェクトをもう 1 つ作成します。 このプロジェクトは、生成された保持する`TableAdapter`s と呼びます、*データ アクセス層*アプリケーション。 データ アクセス層は、データベースへの接続に必要な情報を格納し、通常、中間層に置かれます。  
  
#### <a name="to-create-the-new-class-library-for-the-tableadapters"></a>TableAdapter を保持する新しいクラス ライブラリを作成するには  
  
1.  **ファイル**] メニューの [新しいプロジェクトを NTierWalkthrough ソリューションに追加します。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、**テンプレート**ウィンドウで、をクリックして**クラス ライブラリ**します。  
  
3.  プロジェクトに名前を**DataAccessTier**  をクリック**OK**します。  
  
     DataAccessTier プロジェクトが作成され、NTierWalkthrough ソリューションに追加されます。  
  
## <a name="creating-the-dataset"></a>データセットの作成  
 次に、型指定されたデータセットを作成します。 型指定されたデータセットは、データセット クラス (DataTable クラスを含む) と `TableAdapter` クラスの両方を含む単一のプロジェクトとして作成されます  (すべてのクラスが 1 つのファイルに生成されます)。データセットと `TableAdapter` を別個のプロジェクトに分離すると、データセット クラスが別のプロジェクトに移動し、`TableAdapter` クラスは元のプロジェクトに残ります。 このため、最終的に `TableAdapter` が含まれるプロジェクト (DataAccessTier プロジェクト) にデータセットを作成します。 使用して、データセットを作成するが、**データ ソース構成ウィザード**します。  
  
> [!NOTE]
>  接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。 Northwind サンプル データベースを設定する方法については、次を参照してください。[方法: サンプル データベースをインストール](../data-tools/how-to-install-sample-databases.md)します。  
  
#### <a name="to-create-the-dataset"></a>データセットを作成するには  
  
1.  [DataAccessTier] をクリックして**ソリューション エクスプ ローラー**します。  
  
2.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。  
  
3.  **データソース**ウィンドウで、をクリックして**新しいデータ ソースの追加**を開始する、**データ ソース構成ウィザード**。  
  
4.  **データ ソースの種類を選択**] ページで [**データベース**順にクリックします**次**します。  
  
5.  **データ接続の選択**ページで、次の操作のいずれかを実行します。  
  
     Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は、これをクリックします。  
  
     - または -  
  
     クリックして**新しい接続**を開く、**接続の追加** ダイアログ ボックス。  
  
6.  データベースにパスワードが必要な場合は、該当するオプションを選択して重要情報を含め、 **[次へ]** をクリックします。  
  
    > [!NOTE]
    >  SQL Server に接続するのではなく、ローカル データベース ファイルを選択した場合は、ファイルをプロジェクトに追加するかどうかをたずねるメッセージが表示されます。 クリックして**はい**データベース ファイルをプロジェクトに追加します。  
  
7.  をクリックして**次**で、**アプリケーション構成ファイルへの接続文字列を保存**ページ。  
  
8.  **[データベース オブジェクトの選択]** ページの **[テーブル]** ノードを展開します。  
  
9. チェック ボックスをクリックして、**顧客**と**注文**テーブル、およびクリック**完了**します。  
  
     NorthwindDataSet が DataAccessTier プロジェクトに追加されに表示されます、**データソース**ウィンドウ。  
  
## <a name="separating-the-tableadapters-from-the-dataset"></a>データセットと TableAdapter の分離  
 データセットを作成したら、生成されたデータセット クラスを TableAdapter から分離します。 これを行う、 **DataSet プロジェクト**プロパティを分離されたデータセット クラスを格納するためのプロジェクトの名前にします。  
  
#### <a name="to-separate-the-tableadapters-from-the-dataset"></a>データセットと TableAdapter を分離するには  
  
1. ダブルクリック**NorthwindDataSet.xsd**で**ソリューション エクスプ ローラー**でデータセットを開きます、**データセット デザイナー**します。  
  
2. デザイナーの空の領域をクリックします。  
  
3. 検索、 **DataSet プロジェクト**内のノード、**プロパティ**ウィンドウ。  
  
4. **DataSet プロジェクト**一覧で、 **DataEntityTier**します。  
  
5. **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。  
  
   データセットと TableAdapter が、2 つのクラス ライブラリ プロジェクトに分離されます。 最初にデータセット全体 (DataAccessTier) を含んでいたプロジェクトには、現在は TableAdapter しか含まれません。 指定したプロジェクト、 **DataSet プロジェクト**プロパティ (DataEntityTier) に型指定されたデータセットが含まれています。 (NorthwindDataSet.Dataset.Designer.vb または NorthwindDataSet.Dataset.Designer.cs)。  
  
> [!NOTE]
>  データセットと Tableadapter を分離する場合 (設定して、 **DataSet プロジェクト**プロパティ)、プロジェクト内の既存のデータセット部分クラスが自動的に移動されません。 既存のデータセット部分クラスは、手動でデータセット プロジェクトに移動する必要があります。  
  
## <a name="creating-a-new-service-application"></a>新しいサービス アプリケーションの作成  
 このチュートリアルでは WCF サービスを使用してデータ アクセス層にアクセスする方法を説明するので、新しい WCF サービス アプリケーションを作成します。  
  
#### <a name="to-create-a-new-wcf-service-application"></a>新しい WCF サービス アプリケーションを作成するには  
  
1.  **ファイル**] メニューの [新しいプロジェクトを NTierWalkthrough ソリューションに追加します。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、**プロジェクトの種類**ウィンドウで、をクリックして**WCF**します。 **テンプレート**ウィンドウで、をクリックして**WCF サービス ライブラリ**します。  
  
3.  プロジェクトに名前を**DataService**  をクリック**OK**します。  
  
     DataService プロジェクトが作成されて NTierWalkthrough ソリューションに追加されます。  
  
## <a name="creating-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Customers および Orders のデータを返すデータ アクセス層のメソッドの作成  
 データ サービスは、データ アクセス層の 2 つのメソッド (GetCustomers および GetOrders) を呼び出す必要があります。 これらのメソッドは、Northwind の Customers テーブルと Orders テーブルを返します。 GetCustomers メソッドと GetOrders メソッドは、DataAccessTier プロジェクトに作成します。  
  
#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Customers テーブルを返すメソッドをデータ アクセス層に作成するには  
  
1.  **ソリューション エクスプ ローラー**、NorthwindDataset.xsd でデータセットを開きをダブルクリックして、[の作成と型指定されたデータセットの編集](../data-tools/creating-and-editing-typed-datasets.md)します。  
  
2.  CustomersTableAdapter を右クリックし、をクリックして**クエリの追加**を開く、 [TableAdapters の編集](../data-tools/editing-tableadapters.md)します。  
  
3.  **コマンドの種類を選択** ページで、既定値のままにして**SQL ステートメントを使用** をクリック**次**。  
  
4.  **クエリの種類を選択** ページで、既定値のままにして**を行を返す SELECT**  をクリック**次**。  
  
5.  **SQL SELECT ステートメントを指定して** ページで、既定のクエリのままにしてをクリックして**次**します。  
  
6.  **生成するメソッドの選択**ページで、入力**GetCustomers**の**メソッド名**で、 **DataTable を返す**セクション。  
  
7.  **[完了]** をクリックします。  
  
#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Orders テーブルを返すメソッドをデータ アクセス層に作成するには  
  
1.  OrdersTableAdapter を右クリックし、をクリックして**クエリの追加**します。  
  
2.  **コマンドの種類を選択** ページで、既定値のままにして**SQL ステートメントを使用** をクリック**次**。  
  
3.  **クエリの種類を選択** ページで、既定値のままにして**を行を返す SELECT**  をクリック**次**。  
  
4.  **SQL SELECT ステートメントを指定して** ページで、既定のクエリのままにしてをクリックして**次**します。  
  
5.  **生成するメソッドの選択**ページで、入力**GetOrders**の**メソッド名**で、 **DataTable を返す**セクション。  
  
6.  **[完了]** をクリックします。  
  
7.  **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。  
  
## <a name="adding-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>データ サービスへの、データ エンティティ層およびデータ アクセス層への参照の追加  
 データ サービスはデータセットと TableAdapter の情報を必要とするため、DataEntityTier プロジェクトおよび DataAccessTier プロジェクトへの参照を追加します。  
  
#### <a name="to-add-references-to-the-data-service"></a>データ サービスに参照を追加するには  
  
1.  DataService を右クリックして**ソリューション エクスプ ローラー**クリック**参照の追加**。  
  
2.  をクリックして、**プロジェクト** タブで、**参照の追加** ダイアログ ボックス。  
  
3.  両方を選択、 **DataAccessTier**と**DataEntityTier**プロジェクト。  
  
4.  **[OK]** をクリックします。  
  
## <a name="adding-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>データ アクセス層の GetCustomers メソッドおよび GetOrders メソッドを呼び出す関数のサービスへの追加  
 これで、データを返すメソッドをデータ アクセス層に含めることができました。次に、データ サービスにメソッドを作成して、データ アクセス層のメソッドを呼び出します。  
  
> [!NOTE]
>  C# プロジェクトの場合は、次のコードをコンパイルするために `System.Data.DataSetExtensions` アセンブリへの参照を追加する必要があります。  
  
#### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>データ サービスに GetCustomers 関数と GetOrders 関数を作成するには  
  
1.  **DataService**プロジェクトで、IService1.vb または IService1.cs をダブルクリックします。  
  
2.  次のコードを追加、**ここにサービス操作を追加**コメント。  
  
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
  
3.  DataService プロジェクトで、Service1.vb または Service1.cs をダブルクリックします。  
  
4.  Service1 クラスに次のコードを追加します。  
  
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
  
5.  **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。  
  
## <a name="creating-a-presentation-tier-to-display-data-from-the-data-service"></a>データ サービスのデータを表示するプレゼンテーション層の作成  
 これで、データ アクセス層を呼び出すメソッドを持つデータ サービスをソリューションに含めることができました。次に、データ サービスを呼び出してデータをユーザーに表示する別のプロジェクトを作成します。 このチュートリアルでは、Windows フォーム アプリケーションを作成します。これは n 層アプリケーションのプレゼンテーション層です。  
  
#### <a name="to-create-the-presentation-tier-project"></a>プレゼンテーション層プロジェクトを作成するには  
  
1.  **ファイル**] メニューの [新しいプロジェクトを NTierWalkthrough ソリューションに追加します。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、**プロジェクトの種類**ウィンドウで、をクリックして**Windows**します。 **[テンプレート]** ペインの **[Windows フォーム アプリケーション]** をクリックします。  
  
3.  プロジェクトに名前を**PresentationTier**  をクリック**OK**します。  
  
4.  PresentationTier プロジェクトが作成され、NTierWalkthrough ソリューションに追加されます。  
  
## <a name="setting-the-presentationtier-project-as-the-startup-project"></a>スタートアップ プロジェクトとしての PresentationTier プロジェクトの設定  
 プレゼンテーション層は、データを提示して対話するために使用する実際のクライアント アプリケーションです。このため、PresentationTier プロジェクトをスタートアップ プロジェクトとして設定する必要があります。  
  
#### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>新しいプレゼンテーション層プロジェクトをスタートアップ プロジェクトとして設定するには  
  
-   **ソリューション エクスプ ローラー**を右クリックして**PresentationTier**クリック**スタートアップ プロジェクトとして設定**します。  
  
## <a name="adding-references-to-the-presentation-tier"></a>プレゼンテーション層への参照の追加  
 クライアント アプリケーションである PresentationTier には、サービスのメソッドにアクセスできるように、データ サービスへのサービス参照が必要です。 また、WCF サービスによる型の共有を有効にするために、データセットへの参照も必要です。 データセット部分クラスに追加したコードは、データ サービスを介した型の共有を有効にするまで、プレゼンテーション層で使用することはできません。 通常は、データ テーブルの行と列の変更イベントに検証などのコードを追加するため、クライアントからこのコードにアクセスすることが必要になります。  
  
#### <a name="to-add-a-reference-to-the-presentation-tier"></a>プレゼンテーション層に参照を追加するには  
  
1.  **ソリューション エクスプ ローラー**PresentationTier を右クリックし、クリックして、**参照の追加**します。  
  
2.  **参照の追加**ダイアログ ボックスで、をクリックして、**プロジェクト**タブ。  
  
3.  選択**DataEntityTier**  をクリック**OK**します。  
  
#### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>プレゼンテーション層にサービス参照を追加するには  
  
1.  **ソリューション エクスプ ローラー**PresentationTier を右クリックし、クリックして、**サービス参照の追加**します。  
  
2.  **サービス参照の追加**ダイアログ ボックスで、をクリックして**Discover**します。  
  
3.  選択**Service1**  をクリック**OK**します。  
  
    > [!NOTE]
    >  現在のコンピューターに複数のサービスがある場合は、このチュートリアルで以前に作成したサービス (GetCustomers メソッドおよび GetOrders メソッドを含むサービス) を選択します。  
  
## <a name="adding-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>フォームへの DataGridView の追加とデータ サービスから返されたデータの表示  
 データ サービスにサービス参照を追加した後、**データソース**ウィンドウは、サービスによって返されるデータが設定されます。  
  
#### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>フォームに 2 つのデータ バインド DataGridView を追加するには  
  
1.  **ソリューション エクスプ ローラー**、PresentationTier プロジェクトを選択します。  
  
2.  **データ ソース**ウィンドウで、展開**NorthwindDataSet**探し、**顧客**ノード。  
  
3.  ドラッグ、**顧客**ノードを Form1 にします。  
  
4.  **データ ソース**ウィンドウで、展開、**顧客**ノードと、関連する検索**注文**ノード (、**注文**で入れ子になったノード**顧客**ノード)。  
  
5.  関連するドラッグ**注文**ノードを Form1 にします。  
  
6.  フォームの空の領域をダブルクリックして、`Form1_Load` イベント ハンドラーを作成します。  
  
7.  `Form1_Load` イベント ハンドラーに次のコードを追加します。  
  
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
  
## <a name="increasing-the-maximum-message-size-allowed-by-the-service"></a>サービスで許可されるメッセージの最大サイズの増加  
 サービスは Customers テーブルと Orders テーブルからデータを返すため、maxReceivedMessageSize の既定値ではデータを保持するのに十分ではなく、この値を大きくする必要があります。 このチュートリアルでは、値を 6553600 に変更します。 クライアントで値を変更すると、サービス参照が自動的に更新されます。  
  
> [!NOTE]
>  既定のサイズが低く設定されているのは、サービス拒否 (DoS) 攻撃を受けるリスクを低減するためです。 詳細については、「<xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>」を参照してください。  
  
#### <a name="to-increase-the-maxreceivedmessagesize-value"></a>maxReceivedMessageSize 値を増やすには  
  
1.  **ソリューション エクスプ ローラー**、PresentationTier プロジェクトの app.config ファイルをダブルクリックします。  
  
2.  検索、 **maxReceivedMessage**サイズ属性を値に変更`6553600`します。  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 アプリケーションを実行します。 データがデータ サービスから取得され、フォームに表示されます。  
  
#### <a name="to-test-the-application"></a>アプリケーションをテストするには  
  
1.  F5 キーを押します。  
  
2.  Customers テーブルと Orders テーブルのデータがデータ サービスから取得され、フォームに表示されます。  
  
## <a name="next-steps"></a>次の手順  
 Windows ベース アプリケーションに関連データを保存した後で、アプリケーションの要件によってはさらに操作を追加する必要があります。 たとえば、このアプリケーションに対して次のような拡張を行うことができます。  
  
-   データセットへの検証の追加。 詳しくは、次を参照してください。[チュートリアル: N 層データ アプリケーションへの検証の追加](http://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)します。  
  
-   サービスへの、データを更新してデータベースに戻す追加メソッドの追加。  
  
## <a name="see-also"></a>関連項目  
 [N 層アプリケーションでデータセットを操作します。](../data-tools/work-with-datasets-in-n-tier-applications.md)   
 [階層更新](../data-tools/hierarchical-update.md)   
 [Visual Studio でのデータへのアクセス](../data-tools/accessing-data-in-visual-studio.md)

