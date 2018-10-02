---
title: 'チュートリアル: Windows フォーム上の関連データの表示 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
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
- displaying data on forms, walkthroughs
- Windows Forms, displaying data
- data [Visual Studio], displaying on Windows Forms
- master-details lists, displaying on Windows Forms
- data [Visual Studio], master-details
- displaying tables, related data
- displaying table data
- displaying table information
ms.assetid: fc4b9055-2bf3-4028-8aad-9489820d69f6
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: be86fa89cd35ff55ed9e454c9453b4d2684f311d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47547550"
---
# <a name="walkthrough-displaying-related-data-on-a-windows-form"></a>チュートリアル: Windows フォームでの関連データの表示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

アプリケーションでは、複数のテーブルから取得したデータ、特に、互いに関連し合うテーブルから取得したデータを操作する場合が多くあります。 つまり、親子関係を操作する場合があります。 たとえば、顧客レコードを選択した場合にその顧客の注文が表示されるフォームを作成する場合などです。 関連付けられたレコードをフォームに表示するには、子 <xref:System.Windows.Forms.BindingSource.DataSource%2A> の <xref:System.Windows.Forms.BindingSource> プロパティを親 <xref:System.Windows.Forms.BindingSource> (子テーブルではない) に設定し、子 <xref:System.Windows.Forms.BindingSource.DataMember%2A> の <xref:System.Windows.Forms.BindingSource> プロパティを、親テーブルと子テーブルを相互に結合するデータ リレーションシップに設定します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   作成、 **Windows アプリケーション**プロジェクト。  
  
-   作成して、アプリケーションでデータセットの構成に基づいて、`Customers`と`Orders`を使用して Northwind データベースのテーブル、[データ ソース構成ウィザード](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)します。  
  
-   `Customers` テーブルのデータを表示するコントロールを追加します。  
  
-   選択した `Orders` に基づいて `Customer` を表示するコントロールを追加します。  
  
-   さまざまな顧客を選択し、その顧客に対して正しい注文が表示されるかどうかを確認して、アプリケーションをテストします。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind サンプル データベースにアクセスします。 サンプル データベースをセットアップするには、次を参照してください。[方法: サンプル データベースをインストール](../data-tools/how-to-install-sample-databases.md)します。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 作成するには、まず、 **Windows アプリケーション**します。  
  
#### <a name="to-create-the-windows-application-project"></a>Windows アプリケーション プロジェクトを作成するには  
  
1.  **ファイル**] メニューの [新しいプロジェクトを作成します。  
  
2.  プロジェクトに `RelatedDataWalkthrough` という名前を付けます。  
  
3.  選択**Windows アプリケーション** をクリック**OK**します。 詳細については、次を参照してください。[クライアント アプリケーション](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)します。  
  
     **RelatedDataWalkthrough**プロジェクトが作成されに追加**ソリューション エクスプ ローラー**します。  
  
## <a name="creating-the-data-source"></a>データ ソースの作成  
 このステップでは、Northwind サンプル データベースの `Customers` テーブルと `Orders` テーブルに基づいて、データセットを作成します。  
  
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
  
8.  選択、**顧客**と**注文**テーブル、およびクリック**完了**。  
  
     **NorthwindDataSet**プロジェクトに追加されて、**顧客**テーブルに表示されます、**データ ソース**ウィンドウ。  
  
## <a name="creating-controls-to-display-data-from-the-customers-table"></a>Customers テーブルのデータを表示するコントロールの作成  
  
#### <a name="to-create-controls-to-display-the-customer-data-parent-records"></a>顧客データ (親レコード) を表示するコントロールを作成するには  
  
1.  **データ ソース**ウィンドウで、**顧客**テーブル、および、ドロップダウン矢印をクリックします。  
  
2.  選択**詳細** メニューから。  
  
3.  メインのドラッグ**顧客**ノードから、**データ ソース**ウィンドウの一番上に**Form1**します。  
  
     説明のラベルが付いたデータ バインド コントロールとレコード間を移動するためのツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) がフォームに表示されます。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、 [CustomersTableAdapter](../data-tools/tableadapter-overview.md)、 <xref:System.Windows.Forms.BindingSource>、および<xref:System.Windows.Forms.BindingNavigator>コンポーネント トレイに表示されます。  
  
## <a name="creating-controls-to-display-data-from-the-orders-table"></a>Orders テーブルのデータを表示するコントロールの作成  
 ![データ ソース ウィンドウの関係を示す](../data-tools/media/datasources2.gif "DataSources2")  
  
#### <a name="to-create-controls-to-display-the-orders-for-each-customer-child-records"></a>各顧客 (子レコード) の注文を表示するコントロールを作成するには  
  
-   **データ ソース**ウィンドウで、展開、**顧客**ノードの最後の列を選択し、**顧客**テーブルでは、展開可能な**注文**ノードの下にドラッグして**Form1**します。  
  
     フォームに <xref:System.Windows.Forms.DataGridView> が追加され、新しい <xref:System.Windows.Forms.BindingSource> (`OrdersBindingSource`) と TableAdapter (`OrdersTableAdapter`) がコンポーネント トレイに追加されます。  
  
    > [!NOTE]
    >  開く、[プロパティ ウィンドウ](../ide/reference/properties-window.md)を選択し、 **OrdersBindingSource**します。 <xref:System.Windows.Forms.BindingSource.DataSource%2A> プロパティと <xref:System.Windows.Forms.BindingSource.DataMember%2A> プロパティを調べ、関連レコードを表示するためのデータ バインディングの設定を確認します。 <xref:System.Windows.Forms.BindingSource.DataSource%2A> は、`CustomersBindingSource` テーブルではなく、<xref:System.Windows.Forms.BindingSource> (親テーブルの `Orders`) に設定されます。 <xref:System.Windows.Forms.BindingSource.DataMember%2A> プロパティは `FK_Orders_Customers` に設定されます。これは、複数のテーブルを関連付ける <xref:System.Data.DataRelation> オブジェクトの名前です。  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
  
#### <a name="to-test-the-application"></a>アプリケーションをテストするには  
  
1.  F5 キーを押してアプリケーションを実行します。  
  
2.  使用してさまざまな顧客を選択して、 **CustomersBindingNavigator**に確認する正しい注文が表示されます、<xref:System.Windows.Forms.DataGridView>します。  
  
## <a name="next-steps"></a>次の手順  
 アプリケーションの要件に応じて、マスター/詳細形式のフォームの作成後に、追加の操作を実行できます。 このチュートリアルには、以下のような拡張を行うことができます。  
  
-   `Customers` テーブルにパラメーター化を追加して `Customers` レコードをフィルター処理します。 これを行うには、データを表示する任意のコントロールを選択して、`Customers`テーブルをスマート タグをクリックし、選択**クエリの追加**します。 完了、[検索条件ビルダー ダイアログ ボックス](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d)します。 詳細については、次を参照してください。[方法: Windows フォーム アプリケーションにパラメーター化クエリを追加](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416)します。  
  
## <a name="see-also"></a>関連項目  
 [データのチュートリアル](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [[データ ソース] ウィンドウ](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [新しいデータ ソースを追加します。](../data-tools/add-new-data-sources.md)   
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [方法: 関連データを Windows フォーム アプリケーション表示します。](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)   
 [BindingSource コンポーネントの概要](http://msdn.microsoft.com/library/be838caf-fcb0-4b68-827f-58b2c04b747f)   
 [BindingNavigator コントロールの概要](http://msdn.microsoft.com/library/4423eede-f8d1-4d02-822f-5bf8432680d0)