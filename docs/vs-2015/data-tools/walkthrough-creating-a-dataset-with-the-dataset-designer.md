---
title: 'チュートリアル: データセット デザイナーでデータセットの作成 |Microsoft Docs'
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
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 1a9d47431497f05fd5538510b39b44298587dd0e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49287366"
---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>チュートリアル : データセット デザイナーでのデータセットの作成
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このチュートリアルで使用してデータセットを作成は、**データセット デザイナー**します。 新しいプロジェクトを作成し、新しい追加のプロセスを実行、**データセット**項目にします。 ウィザードを使用しないで、データベース内のテーブルに基づいてテーブルを作成する方法について説明します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   新しいを作成する**Windows アプリケーション**プロジェクト。  
  
-   空の追加**データセット**プロジェクト項目。  
  
-   使用してデータセットを作成することにより、アプリケーションでデータ ソースの構成の作成と、**データセット デザイナー**します。  
  
-   Northwind データベースへの接続を作成する**サーバー エクスプ ローラー**します。  
  
-   データベース内のテーブルに基づいて、データセットに TableAdapter を持つテーブルを作成します。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind サンプル データベース (SQL Server または Access バージョン) にアクセスします。 詳細については、次を参照してください。[方法: サンプル データベースをインストール](../data-tools/how-to-install-sample-databases.md)します。  
  
## <a name="creating-a-new-windows-application-project"></a>新しい Windows アプリケーション プロジェクトの作成  
  
#### <a name="to-create-a-new-windows-application-project"></a>新しい Windows アプリケーション プロジェクトを作成するには  
  
1.  **ファイル**] メニューの [新しいプロジェクトを作成します。  
  
2.  プログラミング言語を選択して、**プロジェクトの種類**ウィンドウ。  
  
3.  クリックして**Windows アプリケーション**で、**テンプレート**ウィンドウ。  
  
4.  プロジェクトの名前`DatasetDesignerWalkthrough`、 をクリックし、 **OK**します。  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] プロジェクトが追加されます**ソリューション エクスプ ローラー**し、デザイナーで新しいフォームを表示します。  
  
## <a name="adding-a-new-dataset-to-the-application"></a>アプリケーションへの新しいデータセットの追加  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>プロジェクトに新しいデータセット項目を追加するには  
  
1.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。  
  
     **[新しい項目の追加]** ダイアログ ボックスが表示されます。  
  
2.  **テンプレート**のボックス、**新しい項目の追加**ダイアログ ボックスで、をクリックして**データセット**します。  
  
3.  データセットの名前を付けます`NorthwindDataset`、 をクリックし、**追加**します。  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] という名前のファイルを追加**NorthwindDataset.xsd**プロジェクトで開くと、**データセット デザイナー**します。  
  
## <a name="creating-a-data-connection-in-server-explorer"></a>サーバー エクスプローラーでのデータ接続の作成  
  
#### <a name="to-create-a-connection-to-the-northwind-database"></a>Northwind データベースへの接続を作成するには  
  
1.  **ビュー**  メニューのをクリックして**サーバー エクスプ ローラー**します。  
  
2.  **サーバー エクスプ ローラー**、クリックして、**データベースへの接続**ボタンをクリックします。  
  
3.  Northwind サンプル データベースへの接続を作成します。  
  
    > [!NOTE]
    >  このチュートリアルでは、SQL Server バージョンまたは Access バージョンの Northwind に接続できます。  
  
## <a name="creating-the-tables-in-the-dataset"></a>データセットへのテーブルの作成  
 ここでは、データセットにテーブルを追加する方法について説明します。  
  
#### <a name="to-create-the-customers-table"></a>Customers テーブルを作成するには  
  
1.  作成したデータ接続を展開**サーバー エクスプ ローラー**の順に展開し、**テーブル**ノード。  
  
2.  ドラッグ、**顧客**からテーブル**サーバー エクスプ ローラー**上に、**データセット デザイナー**します。  
  
     A**顧客**データ テーブルと**CustomersTableAdapter**データセットに追加されます。  
  
#### <a name="to-create-the-orders-table"></a>Orders テーブルを作成するには  
  
-   ドラッグ、**注文**からテーブル**サーバー エクスプ ローラー**上に、**データセット デザイナー**します。  
  
     **注文**データ テーブル、 **OrdersTableAdapter**との間でデータのリレーションシップ、**顧客**と**注文**テーブルに追加されます、データセット。  
  
#### <a name="to-create-the-orderdetails-table"></a>OrderDetails テーブルを作成するには  
  
-   ドラッグ、 **Order Details**からテーブル**サーバー エクスプ ローラー**上に、**データセット デザイナー**します。  
  
     **Order Details**データ テーブル、 **Order DetailsTableAdapter**との間のリレーションシップ、**注文**と**Order Details**テーブルデータセットに追加されます。  
  
## <a name="next-steps"></a>次の手順  
  
### <a name="to-add-functionality-to-your-application"></a>アプリケーションに機能を追加するには  
  
-   データセットを保存します。  
  
-   項目を選択、**データ ソース**ウィンドウ、フォームにドラッグするとします。 詳細については、次を参照してください。 [Visual Studio でのデータにコントロールを Windows フォームのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)します。  
  
-   TableAdapter に他のクエリを追加します。 詳細については、次を参照してください。[方法: TableAdapter クエリの作成](../data-tools/how-to-create-tableadapter-queries.md)です。  
  
-   データセット内のデータ テーブルの <xref:System.Data.DataTable.ColumnChanging> イベントまたは <xref:System.Data.DataTable.RowChanging> イベントに検証ロジックを追加します。 詳細については、次を参照してください。[検証データセットのデータの](../data-tools/validate-data-in-datasets.md)します。  
  
## <a name="see-also"></a>関連項目  
 [データのチュートリアル](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [データを受信するアプリケーションを準備します。](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでデータの編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [データの保存](../data-tools/saving-data.md)