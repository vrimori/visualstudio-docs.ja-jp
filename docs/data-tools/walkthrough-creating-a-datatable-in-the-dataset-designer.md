---
title: "チュートリアル: データセット デザイナーでの DataTable の作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/19/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.technology: vs-data-tools
ms.openlocfilehash: 0e1328eda7974b7e4ec04df0c4f5bd969cf09de6
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2017
---
# <a name="walkthrough-creating-a-datatable-in-the-dataset-designer"></a>チュートリアル : データセット デザイナーでの DataTable の作成
このチュートリアルで説明を作成する方法、 <xref:System.Data.DataTable> (せずに、TableAdapter) を使用して、**データセット デザイナー**です。 Tableadapter を含むデータ テーブルを作成する方法については、次を参照してください。[作成し、Tableadapter を構成](../data-tools/create-and-configure-tableadapters.md)です。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   新しい Windows フォーム アプリケーション プロジェクトを作成します。  
  
-   アプリケーションに新しいデータセットの追加  
  
-   データセットに新しいデータ テーブルを追加します。  
  
-   データ テーブルに列を追加します。  
  
-   テーブルの主キーの設定  
  
## <a name="creating-a-new-windows-forms-application"></a>新しい Windows フォーム アプリケーションの作成  
  
#### <a name="to-create-a-new-windows-forms-application-project"></a>新しい Windows フォーム アプリケーション プロジェクトを作成するには  
  
1. Visual Studio での**ファイル**メニューの **新規**、**プロジェクト.**.  
  
2. いずれかを展開**Visual c#**または**Visual Basic**左側のペインでを選択し、 **Windows クラシック デスクトップ**です。  

3. 中央のペインで、 **Windows フォーム アプリ**プロジェクトの種類。  

4. プロジェクトに名前を**DataTableWalkthrough**を選択し**OK**です。 
  
     **DataTableWalkthrough**プロジェクトが作成され、追加する**ソリューション エクスプ ローラー**です。  
  
## <a name="adding-a-new-dataset-to-the-application"></a>アプリケーションへの新しいデータセットの追加  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>プロジェクトに新しいデータセット項目を追加するには  
  
1.  **プロジェクト**メニューの **新しい項目の追加.**.  
  
     [新しい項目の追加] ダイアログ ボックスが表示されます。  
  
2.  左側のペインで選択**データ**選択してから、**データセット**中央のペインでします。  
  
3.  **[追加]** をクリックします。  
  
     Visual Studio がという名前のファイルを追加**DataSet1.xsd**プロジェクトでそのソリューションを開きます、**データセット デザイナー**です。  
  
## <a name="adding-a-new-datatable-to-the-dataset"></a>データセットに新しいデータ テーブルを追加します。  
  
#### <a name="to-add-a-new-data-table-to-the-dataset"></a>データセットに新しいデータ テーブルを追加するには  
  
1.  ドラッグ、 **DataTable**から、**データセット**のタブ、**ツールボックス**上に、**データセット デザイナー**です。  
  
     という名前のテーブル**DataTable1**データセットに追加します。  
   
2.  タイトル バーをクリックして**DataTable1**し、名前変更`Music`です。  
  
## <a name="adding-columns-to-the-data-table"></a>データ テーブルに列を追加します。  
  
#### <a name="to-add-columns-to-the-data-table"></a>データ テーブルに列を追加するには  
  
1.  右クリックし、**音楽**テーブル。 をポイント**追加**、クリックして**列**です。  
  
2.  列の名前`SongID`です。  
  
3.  **プロパティ**ウィンドウで、設定、<xref:System.Data.DataColumn.DataType%2A>プロパティを<xref:System.Int16?displayProperty=fullName>です。  
  
4.  このプロセスを繰り返して、次の列を追加します。  
  
     `SongTitle`: <xref:System.String?displayProperty=fullName>  
  
     `Artist`: <xref:System.String?displayProperty=fullName>  
  
     `Genre`: <xref:System.String?displayProperty=fullName>  
  
## <a name="setting-the-primary-key-for-the-table"></a>テーブルの主キーの設定  
すべてのデータ テーブルには、主キーを設定する必要があります。 主キーは、データ テーブル内の特定のレコードを一意に識別します。  
  
#### <a name="to-set-the-primary-key-of-the-data-table"></a>データ テーブルの主キーを設定するには  
  
-   右クリックし、 **SongID**列、およびクリック**主キーの設定**です。  
  
     隣に鍵のアイコンが表示されます、 **SongID**列です。  
  
## <a name="saving-your-project"></a>プロジェクトの保存  
  
#### <a name="to-save-the-datatablewalkthrough-project"></a>DataTableWalkthrough プロジェクトを保存するには  
  
-   **ファイル** メニューのをクリックして**すべて保存**です。  
  
## <a name="see-also"></a>関連項目
[Visual Studio でデータセットを作成および構成する](../data-tools/create-and-configure-datasets-in-visual-studio.md)  
[Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
[データの検証](../data-tools/validate-data-in-datasets.md)   
[データの保存](../data-tools/saving-data.md)   