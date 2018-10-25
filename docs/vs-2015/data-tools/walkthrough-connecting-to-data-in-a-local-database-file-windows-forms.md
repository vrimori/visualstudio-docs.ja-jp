---
title: 'チュートリアル: ローカル データベース ファイル (Windows フォーム) 内のデータへの接続 |Microsoft Docs'
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
- databases, connecting to
- local data, SQL Express
- SQL Express, walkthroughs
- SQL Express, connecting
- data [Visual Studio], local
- data [Visual Studio], connecting to SQL Express
ms.assetid: 5e16b7da-3fdc-4e69-bdb4-e8e700481811
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 71898c88a8d7a1d4a119a7e7a932e295ae12eb34
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49176164"
---
# <a name="walkthrough-connecting-to-data-in-a-local-database-file-windows-forms"></a>チュートリアル: ローカル データベース ファイル内のデータへの接続 (Windows フォーム)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

データセットを作成した後アプリケーションにデータ バインディング コントロールを追加することによって、アプリケーションのローカル データベース ファイルから、すばやく簡単にデータを表示できます。 このチュートリアルでは、次の手順で作成したローカル データベース ファイルからデータを表示します[デザイナーを使用して SQL database を作成する](../data-tools/create-a-sql-database-by-using-a-designer.md)します。 Windows フォーム プロジェクトを作成したら、そのデータベースに接続し、アプリケーションのフォームのデータ グリッドに、Customer テーブルのデータを表示することを指定します。  
  
 Visual Studio 2013 でデータベースを作成する場合、SQL Server 2012 データベース ファイル (.mdf) にアクセスするために SQL Server Express LocalDB エンジンが使用されます。 旧バージョンの Visual Studio では、データベース ファイル (.mdf) にアクセスするために SQL Server Express エンジンが使用されます。 参照してください[ローカル データの概要](../data-tools/local-data-overview.md)します。  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
 このチュートリアルでは、次のタスクについて説明します。  
  
-   [データセットの作成と構成](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_CreateDataset)  
  
-   [データ バインド コントロールを追加します。](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_AddCtrls)  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するには、するには、実行して作成した SampleDatabase.mdf データベースにアクセスが必要です。[デザイナーを使用して SQL database を作成する](../data-tools/create-a-sql-database-by-using-a-designer.md)します。  
  
##  <a name="BKMK_CreateDataset"></a> データセットの作成と構成  
  
#### <a name="to-create-and-configure-a-dataset"></a>データセットを作成して構成するには  
  
1.  Windows フォーム プロジェクトを作成し、名前**connectlocaldata という**します。  
  
     参照してください[クライアント アプリケーション](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)します。  
  
2.  場合、**データソース**ウィンドウが表示されない、shift キーを押し-d Alt キーを選択または、メニュー バーで、**ビュー**、**その他の Windows**、 **データソースの表示**.  
  
3.  **データソース**ウィンドウで、選択、**新しいデータ ソースの追加**リンク。  
  
     **データ ソース構成ウィザード**、選択、 **[次へ]** を既定の設定を受け入れるように 2 回のボタンをクリックします。  
  
4.  **データ接続の選択**ページで、選択、**新しい接続**ボタンをクリックします。  
  
     **データ ソースの選択** ダイアログ ボックスが表示されます。  
  
5.  **データ ソース**一覧で、選択**Microsoft SQL Server データベース ファイル**、選択し、**続行**ボタンをクリックします。  
  
     **接続の追加** ダイアログ ボックスが表示されます。  
  
6.  **データベース ファイルの名前**ボックスを実行して作成したファイルを指定[デザイナーを使用して SQL database を作成](../data-tools/create-a-sql-database-by-using-a-designer.md)、ことも、**参照**クリックし、見つけますそのファイル。  
  
     既定では、ファイルは、ユーザーに\\*YourAccount*\Documents\Visual Studio*バージョン*\Projects\SampleDatabaseWalkthrough\SampleDatabaseWalkthrough します。  
  
7.  **サーバーにログオン**、既定値を受け入れる、選択、 **ok**ボタンをクリックし、選択、 **次へ**ボタンをクリックします。  
  
    > [!NOTE]
    >  ローカル データベース ファイルに接続する場合、データベースのコピーをプロジェクトに作成する、またはデータベース ファイルの現在の場所に接続することができます。 参照してください[方法: プロジェクトでローカル データ ファイルを管理](../data-tools/how-to-manage-local-data-files-in-your-project.md)します。  
  
8.  表示されるダイアログ ボックスで、次のように選択します。**はい**データベース ファイルをプロジェクトにコピーします。  
  
9. **アプリケーション構成ファイルへの接続文字列を保存**ページで、選択、**次**ボタン。  
  
10. **データベース オブジェクトの選択** ページで、展開、**テーブル**ノードを選択、**顧客**と**注文**、チェック ボックスをクリックし選択、**完了**ボタンをクリックします。  
  
     **SampleDatabaseDataSet**がプロジェクトに追加、**顧客**と**注文**に表示されるテーブル、**データ ソース**ウィンドウ。  
  
##  <a name="BKMK_AddCtrls"></a> データ バインド コントロールを追加します。  
  
#### <a name="to-add-data-bound-controls"></a>データ バインディング コントロールを追加するには  
  
1.  メインの移動**顧客**ノードから、**データ ソース**ウィンドウ**Form1**します。  
  
     <xref:System.Windows.Forms.DataGridView> と、レコード間を移動するためのツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) がフォーム上に表示されます。 A [SampleDatabaseDataSet](../data-tools/dataset-tools-in-visual-studio.md)、 [CustomersTableAdapter](../data-tools/tableadapter-overview.md)、 <xref:System.Windows.Forms.BindingSource>、および<xref:System.Windows.Forms.BindingNavigator>コンポーネント トレイに表示されます。  
  
2.  アプリケーションを実行して前のチュートリアルで追加したデータを表示するには、F5 キーを選択します。  
  
3.  黄色の追加 アイコンを選択 (![Windows フォームで [追加] ボタン](../data-tools/media/addrecord.png "AddRecord"))、顧客レコードを追加および変更を保存し、ディスク アイコンを選択する (![Windows フォーム[Save]ボタン](../data-tools/media/saveinwf.png "SaveInWF"))。  
  
4.  これを選択して、赤い削除アイコンを選択し、作成したレコードを削除します (![Windows フォームの削除ボタン](../data-tools/media/deleterecord.png "DeleteRecord"))。  
  
## <a name="next-steps"></a>次の手順  
 作成または内のデータ ソースを開く場合に、データセット内のオブジェクトを変更することができます、[の作成と型指定されたデータセットの編集](../data-tools/creating-and-editing-typed-datasets.md)します。 さらに、データセット内のデータ テーブルの <xref:System.Data.DataTable.ColumnChanging> イベントまたは <xref:System.Data.DataTable.RowChanging> イベントに検証ロジックを追加できます。 参照してください[検証データセットのデータの](../data-tools/validate-data-in-datasets.md)します。  
  
## <a name="see-also"></a>関連項目  
 [ローカル データの概要](../data-tools/local-data-overview.md)   
 [方法: プロジェクトでローカル データ ファイルの管理](../data-tools/how-to-manage-local-data-files-in-your-project.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [データを受信するアプリケーションを準備します。](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでデータの編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [データの保存](../data-tools/saving-data.md)