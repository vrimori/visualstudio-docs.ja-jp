---
title: "チュートリアル: データセット デザイナーでデータセットの作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/11/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: f826f7d33a8d35719afacb053995629433b27642
ms.sourcegitcommit: e951faab601f5c05ad6606d8fd0cd2059fc4cc25
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2017
---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>チュートリアル : データセット デザイナーでのデータセットの作成

このチュートリアルで使用するデータセットを作成は、**データセット デザイナー**です。 新しいプロジェクトを作成し、新しい追加の手順に従ってかかる**データセット**に項目。 ウィザードを使用しないで、データベース内のテーブルに基づいてテーブルを作成する方法について説明します。  

このチュートリアルでは、以下のタスクを行います。  

-   新たに作成する**Windows フォーム アプリケーション**プロジェクト。  

-   空の追加**データセット**プロジェクト項目です。  

-   使用してデータセットを作成して、アプリケーションでデータ ソースの構成の作成と、**データセット デザイナー**です。  
 
-   Northwind データベースへの接続を作成する**サーバー エクスプ ローラー**です。  

-   データベース内のテーブルに基づいて、データセットに TableAdapter を持つテーブルを作成します。  

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
このチュートリアルでは、SQL Server Express LocalDB と、Northwind サンプル データベースを使用します。  
  
1.  SQL Server Express LocalDB をお持ちでない場合は、インストールのいずれかから、 [SQL Server のエディションのダウンロード ページ](https://www.microsoft.com/en-us/server-cloud/Products/sql-server-editions/sql-server-express.aspx)、または、 **Visual Studio インストーラー**です。 一部として、Visual Studio インストーラーで、SQL Server Express LocalDB をインストールすることができます、**データ ストレージと処理**ワークロード、または個々 のコンポーネントとして。  
  
2.  次の手順に従って、Northwind サンプル データベースをインストールします。  

    1. Visual Studio で開く、 **SQL Server オブジェクト エクスプ ローラー**ウィンドウです。 (の一部として SQL Server オブジェクト エクスプ ローラーがインストールされている、**データ ストレージと処理**Visual Studio インストーラーでのワークロードです)。展開して、 **SQL Server**ノード。 LocalDB インスタンスを右クリックし、選択**新しいクエリしています.**.  

       クエリ エディター ウィンドウが開きます。  

    2. コピー、 [Northwind TRANSACT-SQL スクリプト](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true)をクリップボードにします。 この T-SQL スクリプトは、最初から、Northwind データベースを作成し、データを設定します。  

    3. T-SQL スクリプトをクエリ エディターに貼り付けを選択し、 **Execute**ボタンをクリックします。  

       短期間のうち、クエリの実行が終了し、Northwind データベースを作成します。  
  
## <a name="creating-a-new-windows-forms-application-project"></a>新しい Windows フォーム アプリケーション プロジェクトを作成します。  
  
#### <a name="to-create-a-new-windows-forms-application-project"></a>新しい Windows フォーム アプリケーション プロジェクトを作成するには  
  
1. Visual Studio での**ファイル**メニューの **新規**、**プロジェクト.**.  
  
2. いずれかを展開**Visual c#**または**Visual Basic**左側のペインでを選択し、 **Windows クラシック デスクトップ**です。  

3. 中央のペインで、 **Windows フォーム アプリ**プロジェクトの種類。  

4. プロジェクトに名前を**DatasetDesignerWalkthrough**を選択し**OK**です。  
  
     Visual Studio にプロジェクトが追加**ソリューション エクスプ ローラー**し、デザイナーで新しいフォームを表示します。  
  
## <a name="adding-a-new-dataset-to-the-application"></a>アプリケーションへの新しいデータセットの追加  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>プロジェクトに新しいデータセット項目を追加するには  
  
1.  **プロジェクト**メニューの **新しい項目の追加.**.  
  
     **[新しい項目の追加]** ダイアログ ボックスが表示されます。  
  
2.  左側のペインで選択**データ**選択してから、**データセット**中央のペインでします。  
  
3.  データセットの名前を付けます**NorthwindDataset**を選択し**追加**です。  
  
     Visual Studio がという名前のファイルを追加**NorthwindDataset.xsd**プロジェクトでそのソリューションを開きます、**データセット デザイナー**です。  
  
## <a name="creating-a-data-connection-in-server-explorer"></a>サーバー エクスプローラーでのデータ接続の作成  
  
#### <a name="to-create-a-connection-to-the-northwind-database"></a>Northwind データベースへの接続を作成するには  
  
1.  **ビュー**  メニューのをクリックして**サーバー エクスプ ローラー**です。  
  
2.  **サーバー エクスプ ローラー**をクリックして、**データベースへの接続**ボタンをクリックします。  
  
3.  Northwind サンプル データベースへの接続を作成します。  
  
## <a name="creating-the-tables-in-the-dataset"></a>データセットへのテーブルの作成  
このセクションでは、データセットにテーブルを追加する方法について説明します。  
  
#### <a name="to-create-the-customers-table"></a>Customers テーブルを作成するには  
  
1.  作成したデータ接続を展開**サーバー エクスプ ローラー**の順に展開し、**テーブル**ノード。  
  
2.  ドラッグ、**顧客**からテーブル**サーバー エクスプ ローラー**上に、**データセット デザイナー**です。  
  
     A**顧客**データ テーブルと**CustomersTableAdapter**データセットに追加されます。  
  
#### <a name="to-create-the-orders-table"></a>Orders テーブルを作成するには  
  
-   ドラッグ、 **Orders**からテーブル**サーバー エクスプ ローラー**上に、**データセット デザイナー**です。  
  
     **Orders**データ テーブル、 **OrdersTableAdapter**との間でデータのリレーションシップ、**顧客**と**Orders**テーブルに追加されます、データセットです。  
  
#### <a name="to-create-the-orderdetails-table"></a>OrderDetails テーブルを作成するには  
  
-   ドラッグ、 **Order Details**からテーブル**サーバー エクスプ ローラー**上に、**データセット デザイナー**です。  
  
     **Order Details**データ テーブル、 **OrderDetailsTableAdapter**との間でデータのリレーションシップ、 **Orders**と**OrderDetails**テーブルデータセットに追加されます。  
  
## <a name="next-steps"></a>次の手順  
  
### <a name="to-add-functionality-to-your-application"></a>アプリケーションに機能を追加するには  
  
-   データセットを保存します。  
  
-   内の項目を選択、**データ ソース**ウィンドウ、フォームにドラッグします。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールを Windows フォームのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)です。  
  
-   TableAdapter に他のクエリを追加します。 
  
-   データセット内のデータ テーブルの <xref:System.Data.DataTable.ColumnChanging> イベントまたは <xref:System.Data.DataTable.RowChanging> イベントに検証ロジックを追加します。 詳細については、次を参照してください。[データセット内のデータを検証](../data-tools/validate-data-in-datasets.md)です。  
  
## <a name="see-also"></a>関連項目
[Visual Studio でデータセットを作成および構成する](../data-tools/create-and-configure-datasets-in-visual-studio.md)  
[Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
[Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
[データの検証](../data-tools/validate-data-in-datasets.md)   
[データの保存](../data-tools/saving-data.md)