---
title: "チュートリアル : データセット デザイナーでの DataTable の作成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "データ [Visual Studio], データセット デザイナー"
  - "データセット デザイナー, 作成 (データ テーブルを)"
  - "DataTable オブジェクト, 作成"
  - "テーブル [Visual Studio], 作成"
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# チュートリアル : データセット デザイナーでの DataTable の作成
このチュートリアルでは、データセット デザイナーを使用して、TableAdapter がない <xref:System.Data.DataTable> を作成する方法を説明します。  TableAdapter を含むデータ テーブルの作成方法については、「[方法 : TableAdapter を作成する](../data-tools/create-and-configure-tableadapters.md)」を参照してください。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   新しい Windows アプリケーション プロジェクトの作成  
  
-   アプリケーションへの新しいデータセットの追加  
  
-   データセットへの新しいデータ テーブルの追加  
  
-   データ テーブルへの列の追加  
  
-   テーブルの主キーの設定  
  
## 新しい Windows アプリケーションの作成  
  
#### 新しい Windows アプリケーション プロジェクトを作成するには  
  
1.  **\[ファイル\]** メニューで新しいプロジェクトを作成します。  
  
2.  **\[プロジェクトの種類\]** ペインでプログラミング言語を選択します。  
  
3.  **\[テンプレート\]** ペインの **\[Windows アプリケーション\]** をクリックします。  
  
4.  プロジェクトに「`DataTableWalkthrough`」という名前を付け、**\[OK\]** をクリックします。  
  
     Visual Studio によってソリューション エクスプローラーにプロジェクトが追加され、デザイナーに **Form1** が表示されます。  
  
## アプリケーションへの新しいデータセットの追加  
  
#### プロジェクトに新しいデータセット項目を追加するには  
  
1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  
  
     \[新しい項目の追加\] ダイアログ ボックスが表示されます。  
  
2.  **\[テンプレート\]** ボックスの **\[データセット\]** を選択します。  
  
3.  **\[追加\]** をクリックします。  
  
     Visual Studio によって **DataSet1.xsd** という名前のファイルがプロジェクトに追加され、データセット デザイナーで開かれます。  
  
## データセットへの新しいデータ テーブルの追加  
  
#### データセットに新しいデータ テーブルを追加するには  
  
1.  **ツールボックス**の **\[データセット\]** タブから**データセット デザイナー**に、**\[DataTable\]** をドラッグします。  
  
     **DataTable1** という名前のテーブルがデータセットに追加されます。  
  
    > [!NOTE]
    >  TableAdapter を含むデータ テーブルの作成方法については、「[チュートリアル : 複数のクエリによる TableAdapter の作成](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)」を参照してください。  
  
2.  **DataTable1** のタイトル バーをクリックし、「`Music`」に変更します。  
  
## データ テーブルへの列の追加  
  
#### データ テーブルに列を追加するには  
  
1.  **Music** テーブルを右クリックします。  **\[追加\]** をポイントし、**\[列\]** をクリックします。  
  
2.  列に「`SongID`」という名前を付けます。  
  
3.  **\[プロパティ\]** ウィンドウで、<xref:System.Data.DataColumn.DataType%2A> プロパティを <xref:System.Int16?displayProperty=fullName> に設定します。  
  
4.  この手順を繰り返して、次の列を追加します。  
  
     `SongTitle` : <xref:System.String?displayProperty=fullName>  
  
     `Artist` : <xref:System.String?displayProperty=fullName>  
  
     `Genre` : <xref:System.String?displayProperty=fullName>  
  
## テーブルの主キーの設定  
 すべてのデータ テーブルには、主キーが必要です。  主キーは、データ テーブル内の特定のレコードを一意に識別します。  
  
#### データ テーブルの主キーを設定するには  
  
-   **SongID** 列を右クリックし、**\[主キーの設定\]** をクリックします。  
  
     キー アイコンが **SongID** 列の隣に表示されます。  
  
## プロジェクトの保存  
  
#### DataTableWalkthrough プロジェクトを保存するには  
  
-   **\[ファイル\]** メニューの **\[すべてを保存\]** をクリックします。  
  
## 次の手順  
 テーブルを作成したので、次の操作を実行できます。  
  
|目的|参照項目|  
|--------|----------|  
|データ入力用フォームの作成|[チュートリアル: Windows フォームでのデータの表示](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).|  
|テーブルへのデータの追加|[DataTable へのデータの追加](../Topic/Adding%20Data%20to%20a%20DataTable.md).|  
|テーブル内のデータの表示|[DataTable 内のデータの表示](../Topic/Viewing%20Data%20in%20a%20DataTable.md).|  
|データの編集|[DataTable の編集](../Topic/DataTable%20Edits.md)|  
|テーブルからの行の削除|[DataRow の削除](../Topic/DataRow%20Deletion.md)|  
  
## 参照  
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)   
 [データに関するチュートリアル](../Topic/Data%20Walkthroughs.md)