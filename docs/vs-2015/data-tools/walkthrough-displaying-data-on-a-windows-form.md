---
title: 'チュートリアル: Windows フォームでのデータの表示 |Microsoft Docs'
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
- Windows applications, displaying data
- data binding, Windows Forms
- data [Visual Studio], displaying on Windows Forms
- forms, displaying data
ms.assetid: f6e08c2c-c792-43de-adf3-3e52c0100225
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 3decf0da6dd6d16c0128fdaeedf2fcd0cea94871
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47545731"
---
# <a name="walkthrough-displaying-data-on-a-windows-form"></a>チュートリアル: Windows フォームでのデータの表示
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

アプリケーション開発で最も一般的なシナリオの 1 つは、Windows ベースのアプリケーションのフォームにデータを表示することです。 項目をドラッグしてフォームにデータを表示することができます、[データ ソース ウィンドウ](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)フォーム上にします。 このチュートリアルでは、単一のテーブルのデータを、複数の各コントロールに表示する簡単なフォームを作成します。 この例では、Northwind サンプル データベースの `Customers` テーブルを使用します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   新しいを作成する**Windows アプリケーション**プロジェクト。  
  
-   作成と構成を含むデータセット、[データ ソース構成ウィザード](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f)します。  
  
-   項目をドラッグしたときに、フォームに作成するコントロールを選択すると、**データソース**ウィンドウ。 詳細については、次を参照してください。[設定、データ ソース ウィンドウからドラッグするときに作成されるコントロール](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)します。  
  
-   項目をドラッグして、データ バインド コントロールを作成、**データソース**ウィンドウから、フォームにします。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Northwind サンプル データベースにアクセスします。 詳細については、次を参照してください。[方法: サンプル データベースをインストール](../data-tools/how-to-install-sample-databases.md)します。  
  
## <a name="creating-the-windows-application"></a>Windows アプリケーションの作成  
 作成するには、まず、 **Windows アプリケーション**プロジェクト。  
  
#### <a name="to-create-the-new-windows-application-project"></a>新しい Windows アプリケーション プロジェクトを作成するには  
  
1.  **ファイル**] メニューの [新しいプロジェクトを作成します。  
  
2.  プロジェクトに `DisplayingDataonaWindowsForm` という名前を付けます。  
  
3.  選択**Windows アプリケーション** をクリック**OK**します。 詳細については、次を参照してください。[クライアント アプリケーション](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)します。  
  
     **DisplayingDataonaWindowsForm**プロジェクトが作成されに追加**ソリューション エクスプ ローラー**します。  
  
## <a name="creating-the-data-source"></a>データ ソースの作成  
 この手順を使用してデータ ソースを作成し、**データ ソース構成ウィザード**に基づいて、 `Customers` Northwind サンプル データベース内のテーブル。 接続を作成するには、Northwind サンプル データベースへのアクセス権を持っている必要があります。 Northwind サンプル データベースのセットアップについては、次を参照してください。[方法: サンプル データベースをインストール](../data-tools/how-to-install-sample-databases.md)します。  
  
#### <a name="to-create-the-data-source"></a>データ ソースを作成するには  
  
1.  **[データ]** メニューの **[データ ソースの表示]** をクリックします。  
  
2.  **データソース**ウィンドウで、**新しいデータ ソースの追加**を開始する、**データ ソース構成ウィザード**します。  
  
3.  **[データソースの種類を選択]** ページで、 **[データベース]** をクリックし、 **[次へ]** をクリックします。  
  
4.  **データ接続の選択**ページは、次のいずれか。  
  
    -   Northwind サンプル データベースへのデータ接続がドロップダウン リストに表示されている場合は選択します。  
  
         - または -  
  
    -   選択**新しい接続**を起動する、**接続の追加/変更** ダイアログ ボックス.  
  
5.  データベースにパスワードが必要な場合をクリックして、機密データを含めるオプションを選択**次**します。  
  
6.  をクリックして**次**で、**接続文字列をアプリケーション構成ファイルに保存**ページ。  
  
7.  展開、**テーブル**上のノード、**データベース オブジェクトの選択**ページ。  
  
8.  選択、**顧客**テーブルをクリックして**完了**。  
  
     **NorthwindDataSet**プロジェクトに追加されて、**顧客**テーブルに表示されます、**データ ソース**ウィンドウ。  
  
## <a name="setting-the-controls-to-be-created"></a>作成するコントロールの設定  
 このチュートリアルでは、データになります、**詳細**レイアウトの個々 のコントロールにデータが表示されます。 (別の方法は、既定**グリッド**レイアウトでデータを表示する場所を<xref:System.Windows.Forms.DataGridView>コントロールです)。  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>[データ ソース] ウィンドウの項目にドロップ タイプを設定するには  
  
1.  展開、**顧客**内のノード、**データソース**ウィンドウ。  
  
2.  ドロップ タイプを変更、**顧客**テーブル**詳細**を選択して**詳細**でドロップダウン リストから、**顧客**ノード。 詳細については、次を参照してください。[設定、データ ソース ウィンドウからドラッグするときに作成されるコントロール](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)します。  
  
3.  変更、 **CustomerID**列のドロップ タイプを選択して、ラベルを**ラベル**コントロール リストから、 **CustomerID**ノード。  
  
## <a name="creating-the-form"></a>フォームの作成  
 項目をドラッグして、データ バインド コントロールを作成、**データソース**ウィンドウから、フォームにします。  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>フォームにデータ バインド コントロールを作成するには  
  
-   メインのドラッグ**顧客**ノードから、**データ ソース**ウィンドウから、フォームにします。  
  
     説明のラベルが付いたデータ バインド コントロールとレコード間を移動するためのツール ストリップ (<xref:System.Windows.Forms.BindingNavigator>) がフォームに表示されます。 A [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md)、 [CustomersTableAdapter](../data-tools/tableadapter-overview.md)、 <xref:System.Windows.Forms.BindingSource>、および<xref:System.Windows.Forms.BindingNavigator>コンポーネント トレイに表示されます。  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
  
#### <a name="to-run-the-application"></a>アプリケーションを実行するには  
  
-   F5 キーを押します。  
  
-   <xref:System.Windows.Forms.BindingNavigator> コントロールを使用してレコード間を移動します。  
  
## <a name="next-steps"></a>次の手順  
 アプリケーションの要件に応じて、データをバインドした Windows フォームの作成後に、追加の操作を実行できます。 このチュートリアルで行うことができる拡張には次のものがあります。  
  
-   フォームに検索機能を追加します。 詳細については、次を参照してください。[方法: Windows フォーム アプリケーションにパラメーター化クエリを追加](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416)します。  
  
-   データベースに更新を送信する機能を追加できます。 詳細については、次を参照してください。[チュートリアル: データベース (1 つのテーブル) にデータを保存する](http://msdn.microsoft.com/library/68befa96-7463-43e8-abcf-dc2f42ccd53d)します。  
  
-   追加、`Orders`テーブルを選択してデータセットを**ウィザードで DataSet を構成**内から、**データソース**ウィンドウ。 ドラッグして関連データを表示するコントロールを追加することができ、**注文**ノード (下にある、 **Fax**内の列、**顧客**テーブル) をフォームにします。 詳細については、「[方法: 関連するデータを Windows フォーム アプリケーションに表示する](../data-tools/how-to-display-related-data-in-a-windows-forms-application.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [データのチュートリアル](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [新しいデータ ソースを追加します。](../data-tools/add-new-data-sources.md)   
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)