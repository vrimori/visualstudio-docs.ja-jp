---
title: 'チュートリアル: 複数のクエリによる TableAdapter の作成 |Microsoft Docs'
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
- TableAdapter queries, creating
- data [Visual Studio], TableAdapters
- TableAdapters, creating
- data [Visual Studio], walkthroughs
- queries [Visual Studio], TableAdapters
ms.assetid: f784dc4d-d514-4ade-8226-f8271c5b1ed8
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 4226fc805ed0335109d0a6b98f1235ae46de1664
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206701"
---
# <a name="walkthrough-creating-a-tableadapter-with-multiple-queries"></a>チュートリアル : 複数のクエリによる TableAdapter の作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このチュートリアルでは、データセットを使用して、TableAdapter を作成します、[データ ソース構成ウィザード](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)します。 2 番目のクエリを作成する手順、チュートリアルでは、 [TableAdapter](../data-tools/tableadapter-overview.md)を使用して、 [TableAdapters の編集](../data-tools/editing-tableadapters.md)内、[データセット デザイナー](../data-tools/creating-and-editing-typed-datasets.md)します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   新しいを作成する**Windows アプリケーション**プロジェクト。  
  
-   使用してデータセットを作成することにより、アプリケーションでデータ ソースの構成の作成と、**データ ソース構成ウィザード**します。  
  
-   新しいデータセットを開いて、**データセット デザイナー**します。  
  
-   クエリを使用して TableAdapter に追加、 **TableAdapter クエリ構成ウィザード**します。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind サンプル データベース (SQL Server または Access バージョン) にアクセスします。 詳細については、次を参照してください。[方法: サンプル データベースをインストール](../data-tools/how-to-install-sample-databases.md)します。  
  
## <a name="creating-a-new-windows-application"></a>新しい Windows アプリケーションの作成  
 最初に Windows アプリケーションを作成します。  
  
#### <a name="to-create-a-new-windows-application-project"></a>新しい Windows アプリケーション プロジェクトを作成するには  
  
1.  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]から、**ファイル**] メニューの [新しいプロジェクトを作成します。  
  
2.  プログラミング言語を選択して、**プロジェクトの種類**ウィンドウ。  
  
3.  クリックして**Windows アプリケーション**で、**テンプレート**ウィンドウ。  
  
4.  プロジェクトの名前`TableAdapterQueriesWalkthrough`、 をクリックし、 **OK**します。  
  
     Visual Studio にプロジェクトが追加**ソリューション エクスプ ローラー**し、デザイナーで新しいフォームを表示します。  
  
## <a name="creating-a-database-data-source-with-a-tableadapter"></a>TableAdapter によるデータベース データ ソースと の作成  
 この手順を使用してデータ ソースを作成し、**データ ソース構成ウィザード**に基づいて、 `Customers` Northwind サンプル データベース内のテーブル。 接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。 Northwind サンプル データベースのセットアップについては、次を参照してください。[方法: サンプル データベースをインストール](../data-tools/how-to-install-sample-databases.md)します。  
  
#### <a name="to-create-the-data-source"></a>データ ソースを作成するには  
  
1.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。  
  
2.  **データソース**ウィンドウで、**新しいデータ ソースの追加**を開始する、**データ ソース構成ウィザード**します。  
  
3.  **[データソースの種類を選択]** ページで、 **[データベース]** をクリックし、 **[次へ]** をクリックします。  
  
4.  **データ接続の選択**ページは、次のいずれか。  
  
    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。  
  
         - または -  
  
    -   選択**新しい接続**を起動する、**接続の追加/変更** ダイアログ ボックス。  
  
5.  データベースにパスワードが必要な場合をクリックして、機密データを含めるオプションを選択**次**します。  
  
6.  をクリックして**次**で、**接続文字列をアプリケーション構成ファイルに保存**ページ。  
  
7.  展開、**テーブル**上のノード、**データベース オブジェクトの選択**ページ。  
  
8.  選択、**顧客**テーブルをクリックして**完了**。  
  
     **NorthwindDataSet**プロジェクトに追加されて、**顧客**テーブルに表示されます、**データ ソース**ウィンドウ。  
  
## <a name="opening-the-dataset-in-the-dataset-designer"></a>データセット デザイナーでデータセットを開く  
  
#### <a name="to-open-the-dataset-in-the-dataset-designer"></a>データセット デザイナーでデータセットを開くには  
  
1.  右クリックして**NorthwindDataset**で、**データソース**ウィンドウ。  
  
2.  ショートカット メニューで、**デザイナーで DataSet を編集**します。  
  
     NorthwindDataset が開きます、**データセット デザイナー**します。  
  
## <a name="adding-a-second-query-to-the-customerstableadapter"></a>CustomersTableAdapter への 2 つ目のクエリの追加  
 ウィザードで作成されたデータセットに、**顧客**データ テーブルと**CustomersTableAdapter**します。 チュートリアルのこのセクションに追加する 2 番目のクエリ、 **CustomersTableAdapter**します。  
  
#### <a name="to-add-a-query-to-the-customerstableadapter"></a>CustomersTableAdapter にクエリを追加するには  
  
1.  ドラッグ、**クエリ**から、**データセット**のタブ、**ツールボックス**上に、**顧客**テーブル。  
  
     [TableAdapters の編集](../data-tools/editing-tableadapters.md)が開きます。  
  
2.  選択**SQL ステートメントを使用**、 をクリックし、**次**。  
  
3.  選択**を行を返す SELECT**、順にクリックします**次**します。  
  
4.  クエリに次のように WHERE 句を追加します。  
  
    ```  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax   
    FROM Customers   
    WHERE City = @City  
    ```  
  
    > [!NOTE]
    >  Northwind の Access のバージョンを使用している場合は、置換、@Cityが疑問符付きパラメーター。 (`SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE City = ?`)  
  
5.  **生成するメソッドの選択** ページで、名前、 **Datatable**メソッド`FillByCity`します。  
  
    > [!NOTE]
    >  メソッドを**DataTable を返す**のため、チェック ボックスをオフにしたり、既定の名前、このチュートリアルでは使用されません。  
  
6.  をクリックして**次**し、ウィザードを終了します。  
  
     **FillByCity**にクエリを追加、 **CustomersTableAdapter**します。  
  
## <a name="adding-code-to-execute-the-additional-query-on-the-form"></a>追加のクエリを実行するコードのフォームへの追加  
  
#### <a name="to-execute-the-query"></a>クエリを実行するには  
  
1.  選択**Form1**で**ソリューション エクスプ ローラー**、 をクリック**ビュー デザイナー**します。  
  
2.  ドラッグ、**顧客**ノードから、**データ ソース**ウィンドウ**Form1**します。  
  
3.  選択してコード ビューに変更**コード**から、**ビュー**メニュー。  
  
4.  `Form1_Load` イベント ハンドラー内のコードを、`FillByCity` クエリを実行する以下のコードに置き換えます。  
  
     [!code-csharp[VbRaddataTableAdapters#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form1.cs#1)]
     [!code-vb[VbRaddataTableAdapters#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form1.vb#1)]  
  
## <a name="running-the-application"></a>アプリケーションの実行  
  
#### <a name="to-run-the-application"></a>アプリケーションを実行するには  
  
-   F5 キーを押します。  
  
-   グリッドに、`City` 値が `Seattle` の顧客が読み込まれます。  
  
## <a name="next-steps"></a>次の手順  
  
### <a name="to-add-functionality-to-your-application"></a>アプリケーションに機能を追加するには  
  
-   <xref:System.Windows.Forms.TextBox> コントロールおよび <xref:System.Windows.Forms.Button> コントロールを追加し、テキスト ボックスの値をクエリに渡します。 (`CustomersTableAdapter.FillByCity(NorthwindDataSet.Customers, TextBox1.Text)`).  
  
-   データセット内のデータ テーブルの <xref:System.Data.DataTable.ColumnChanging> イベントまたは <xref:System.Data.DataTable.RowChanging> イベントに検証ロジックを追加します。 詳細については、次を参照してください。[検証データセットのデータの](../data-tools/validate-data-in-datasets.md)します。  
  
## <a name="see-also"></a>関連項目  
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [作成し、Tableadapter を構成します。](../data-tools/create-and-configure-tableadapters.md)   
 [方法: TableAdapter クエリの作成](../data-tools/how-to-create-tableadapter-queries.md)   
 [データのチュートリアル](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [データを受信するアプリケーションを準備します。](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)