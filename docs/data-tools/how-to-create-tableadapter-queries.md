---
title: "方法 : TableAdapter クエリを作成する | Microsoft Docs"
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
  - "データ [Visual Studio], TableAdapter クエリ"
  - "クエリ [Visual Studio], 作成"
  - "クエリ [Visual Studio], TableAdapter"
  - "TableAdapter, 作成 (クエリを)"
ms.assetid: df0cf4a5-e9cc-4de6-8b94-ce74fb7b2452
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 方法 : TableAdapter クエリを作成する
TableAdapter クエリは、アプリケーションからデータベースに対して実行できる SQL ステートメントまたはストアド プロシージャです。  
  
 1 つの TableAdapter に、アプリケーションで必要な数のクエリを追加できます。  TableAdapter クエリは、TableAdapter のメソッドとして表されます。  市の値を表すパラメーターを受け取る `FillByCity` という名前のクエリを作成したとして、そのクエリを TableAdapter に追加します。  これは、正しい型のパラメーター \(この場合は市の値を表す文字列\) を引数として受け取る、型指定されたメソッドとして追加されます。  TableAdapter クエリは、オブジェクトのメソッドの場合と同様に呼び出します。  たとえば、以下のコードは、`FillByCity` クエリを実行して、市の値が `Seattle` である顧客すべてを `Customers` テーブルに格納します。  
  
 [!CODE [VbRaddataTableAdapters#1](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#1)]  
  
 TableAdapter クエリは、データ テーブルに値を設定したり \(`Fill` クエリと `FillBy` クエリ\)、クエリが返すデータを読み込んだ新しいデータ テーブルを返すことができます \(`GetData` クエリと `GetDataBy` クエリ\)。  
  
 [TableAdapter クエリの構成ウィザード](../data-tools/editing-tableadapters.md)を実行すると、クエリを既存の TableAdapter に追加できます。  追加するには、TableAdapter を右クリックし、**\[クエリの追加\]** をクリックします。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## データセット デザイナーでのクエリの作成  
  
#### データセット デザイナーで TableAdapter にクエリを追加するには  
  
1.  **データセット デザイナー**でデータセットを開きます。  詳細については、「[方法 : データセット デザイナーでデータセットを開く](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)」を参照してください。  
  
2.  目的の TableAdapter を右クリックし、**\[クエリの追加\]** をクリックします。  
  
     または  
  
3.  **ツールボックス**の **\[データセット\]** タブからデザイナー上のテーブルに **\[Query\]** をドラッグします。  
  
     **TableAdapter クエリの構成ウィザード**が開きます。  
  
4.  ウィザードが完了し、TableAdapter にクエリが追加されます。  
  
## Windows アプリケーションのフォームにおけるクエリの直接作成  
 フォーム上に TableAdapter のインスタンスがある場合、[ダイアログ ボックス](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md)を使用してクエリを追加できます。この場合、クエリに必要な入力パラメーターを受け取る <xref:System.Windows.Forms.ToolStrip> コントロール、およびクエリを実行するボタンが、フォームに追加されます。  
  
#### \[検索条件\] ダイアログ ボックスを使用して TableAdapter にクエリを追加するには  
  
1.  コンポーネント トレイで TableAdapter を選択します。  
  
2.  TableAdapter のスマート タグをクリックし、**\[クエリの追加\]** をクリックします。  
  
3.  ダイアログ ボックスに必要な項目を入力すると、TableAdapter にクエリが追加されます。  詳細については、「[ダイアログ ボックス](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md)」を参照してください。  
  
## 参照  
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [方法 : TableAdapter クエリを編集する](../data-tools/how-to-edit-tableadapter-queries.md)   
 [型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)   
 [データ ソースの概要](../data-tools/add-new-data-sources.md)   
 [方法 : データベース内のデータに接続する](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [方法 : Windows フォーム BindingNavigator コントロールを使用してデータ間を移動する](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)   
 [チュートリアル: Windows フォームでのデータの表示](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [チュートリアル : 複数のクエリによる TableAdapter の作成](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)