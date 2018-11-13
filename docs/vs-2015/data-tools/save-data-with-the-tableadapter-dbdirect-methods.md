---
title: TableAdapter DBDirect メソッドを使ってデータを保存 |Microsoft Docs
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
- TableAdapters, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], TableAdapter
ms.assetid: 74a6773b-37e1-4d96-a39c-63ee0abf49b1
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6b7a7ec1d244f8bf711f0d1aaf4726c910846357
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219719"
---
# <a name="save-data-with-the-tableadapter-dbdirect-methods"></a>TableAdapter DBDirect メソッドを使用してデータを保存する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
このチュートリアルでは、TableAdapter の DBDirect メソッドを使用して、データベースに対して直接 SQL ステートメントを実行するための詳細な手順を提供します。 TableAdapter の DBDirect メソッドは、細かいレベル、データベースの更新で制御を提供します。 それらを使用するには個別に呼び出すことによって、特定の SQL ステートメントおよびストアド プロシージャを実行する`Insert`、 `Update`、および`Delete`アプリケーションに必要なメソッド (オーバー ロードされたのではなく`Update`更新プログラムを実行するメソッド、INSERT、および 1 回の呼び出しですべての DELETE ステートメント)。  
  
 このチュートリアルでは、次の作業を行う方法について説明します。  
  
-   新規作成**Windows アプリケーション**します。  
  
-   作成し、構成を含むデータセット、[データ ソース構成ウィザード](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)します。  
  
-   コントロールを選択してから項目をドラッグしたときにフォーム上に作成する、**データソース**ウィンドウ。 詳細については、次を参照してください。[設定、データ ソース ウィンドウからドラッグするときに作成されるコントロール](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)します。  
  
-   項目をドラッグして、データ バインド フォームを作成、**データソース**ウィンドウから、フォームにします。  
  
-   直接データベースにアクセスし、挿入、更新、および削除を実行するメソッドを追加するには.  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind サンプル データベースにアクセスします。 詳細については、次を参照してください。[方法: サンプル データベースをインストール](../data-tools/how-to-install-sample-databases.md)します。  
  
## <a name="create-a-windows-application"></a>Windows アプリケーションを作成します。  
 作成するには、まず、 **Windows アプリケーション**します。  
  
#### <a name="to-create-the-new-windows-project"></a>新しい Windows プロジェクトを作成するには  
  
1.  Visual Studio での**ファイル**] メニューの [新規作成**プロジェクト**。  
  
2.  プロジェクトに名前を**TableAdapterDbDirectMethodsWalkthrough**します。  
  
3.  選択**Windows アプリケーション**、し、 **OK**します。 詳細については、次を参照してください。[クライアント アプリケーション](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)します。  
  
     **TableAdapterDbDirectMethodsWalkthrough**プロジェクトが作成されに追加**ソリューション エクスプ ローラー**します。  
  
## <a name="create-a-data-source-from-your-database"></a>データベースからデータ ソースを作成します。  
 このステップでは、**データ ソース構成ウィザード**に基づいてデータ ソースを作成する、 `Region` Northwind サンプル データベース内のテーブル。 接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。 Northwind サンプル データベースの設定の詳細については、次を参照してください。[方法: サンプル データベースをインストール](../data-tools/how-to-install-sample-databases.md)します。  
  
#### <a name="to-create-the-data-source"></a>データ ソースを作成するには  
  
1.  **データ**メニューの  **データ ソースの**します。  
  
2.  **データソース**ウィンドウで、**新しいデータ ソースの追加**を開始する、**データ ソース構成ウィザード**します。  
  
3.  **データ ソースの種類を選択**画面で、**データベース**、し、**次**します。  
  
4.  **データ接続の選択**画面で、次のいずれかの操作を行います。  
  
    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。  
  
         - または -  
  
    -   選択**新しい接続**を起動する、**接続の追加/変更** ダイアログ ボックス。  
  
5.  データベースにパスワードが必要な場合は、機密データを含めるしを選択するオプションを選択**次**します。  
  
6.  **接続文字列をアプリケーション構成ファイルに保存**画面で、**次**します。  
  
7.  **データベース オブジェクトの選択**画面で、展開、**テーブル**ノード。  
  
8.  選択、`Region`テーブルし、**完了**します。  
  
     **NorthwindDataSet**をプロジェクトに追加し、`Region`テーブルに表示されます、**データ ソース**ウィンドウ。  
  
## <a name="addcontrols-to-the-form-to-display-the-data"></a>データを表示するフォームに Addcontrols  
 項目をドラッグして、データ バインド コントロールを作成、**データソース**ウィンドウから、フォームにします。  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Windows フォーム上のコントロールのバインドをデータを作成するには  
  
-   メインのドラッグ**リージョン**ノードから、**データ ソース**ウィンドウから、フォームにします。  
  
     レコード間をナビゲートするための <xref:System.Windows.Forms.DataGridView> コントロールとツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) がフォームに表示されます。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、 [RegionTableAdapter](../data-tools/tableadapter-overview.md)、 <xref:System.Windows.Forms.BindingSource>、および<xref:System.Windows.Forms.BindingNavigator>コンポーネント トレイに表示されます。  
  
#### <a name="to-add-buttons-that-will-call-the-individual-tableadapter-dbdirect-methods"></a>個々の TableAdapter DbDirect メソッドを呼び出すボタンを追加するには  
  
1.  3 つをドラッグして<xref:System.Windows.Forms.Button>コントロールを**ツールボックス**に**Form1** (以下、 **RegionDataGridView**)。  
  
2.  以下の設定を**名前**と**テキスト**各ボタンのプロパティ。  
  
    |名前|テキスト|  
    |----------|----------|  
    |`InsertButton`|**[挿入]**|  
    |`UpdateButton`|**更新**|  
    |`DeleteButton`|**削除**|  
  
#### <a name="to-add-code-to-insert-new-records-into-the-database"></a>データベースに新しいレコードを挿入するコードを追加するには  
  
1.  選択**InsertButton**クリック イベントのイベント ハンドラーを作成し、コード エディターでフォームを開きます。  
  
2.  `InsertButton_Click` イベント ハンドラーを次のコードで置き換えます。  
  
     [!code-csharp[VbRaddataSaving#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#1)]
     [!code-vb[VbRaddataSaving#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#1)]  
  
#### <a name="to-add-code-to-update-records-in-the-database"></a>データベースのレコードを更新するコードを追加するには  
  
1.  ダブルクリックして、 **UpdateButton**クリック イベントのイベント ハンドラーを作成し、コード エディターでフォームを開きます。  
  
2.  `UpdateButton_Click` イベント ハンドラーを次のコードで置き換えます。  
  
     [!code-csharp[VbRaddataSaving#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#2)]
     [!code-vb[VbRaddataSaving#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#2)]  
  
#### <a name="to-add-code-to-delete-records-from-the-database"></a>データベースからレコードを削除するコードを追加するには  
  
1.  選択**DeleteButton**クリック イベントのイベント ハンドラーを作成し、コード エディターでフォームを開きます。  
  
2.  `DeleteButton_Click` イベント ハンドラーを次のコードで置き換えます。  
  
     [!code-csharp[VbRaddataSaving#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form1.cs#3)]
     [!code-vb[VbRaddataSaving#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form1.vb#3)]  
  
## <a name="run-the-application"></a>アプリケーションの実行  
  
#### <a name="to-run-the-application"></a>アプリケーションを実行するには  
  
-   選択**F5**アプリケーションを実行します。  
  
-   選択、**挿入**ボタンをクリックし、新しいレコードがグリッドに表示されることを確認します。  
  
-   選択、 **Update**ボタンをクリックし、グリッドのレコードが更新されることを確認します。  
  
-   選択、**削除**ボタンをクリックし、グリッドからレコードが削除されることを確認します。  
  
## <a name="next-steps"></a>次の手順  
 アプリケーションの要件によっては、データ バインド フォームの作成後に実行する場合があります。 このチュートリアルで行うことができる拡張には次のものがあります。  
  
-   フォームに検索機能を追加します。 詳細については、次を参照してください。[方法: Windows フォーム アプリケーションにパラメーター化クエリを追加](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416)します。  
  
-   データセットにテーブルを選択して追加**ウィザードで DataSet を構成**内から、**データソース**ウィンドウ。 関連するコードをフォームにドラッグすることによって、関連するデータを表示するコントロールを追加できます。 詳細については、「[方法: 関連するデータを Windows フォーム アプリケーションに表示する](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [データをデータベースに保存する](../data-tools/save-data-back-to-the-database.md)

