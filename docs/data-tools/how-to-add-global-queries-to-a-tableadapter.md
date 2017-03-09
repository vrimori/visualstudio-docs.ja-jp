---
title: "方法 : データセットにグローバル クエリを追加する | Microsoft Docs"
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
  - "データ [Visual Studio], TableAdapter"
  - "データセット [Visual Basic], グローバル関数"
  - "データセット [Visual Basic], スカラー関数"
  - "グローバル関数, データセット"
  - "クエリ [Visual Studio], TableAdapter"
  - "スカラー関数, データセット"
  - "TableAdapter クエリ"
  - "TableAdapter クエリの構成ウィザード"
  - "TableAdapter, グローバル クエリ"
ms.assetid: 4abffd6b-2e9f-4ef3-99b2-6e9ae4ad4679
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# 方法 : データセットにグローバル クエリを追加する
*グローバル クエリ*は、単一の \(スカラー\) 値を返すか、または値を返さない SQL クエリです。  通常、グローバル関数は、情報の挿入、更新、削除、および集計 \(たとえばテーブル内の顧客数や特定の注文におけるすべての項目の総額\) などのデータベース操作を実行します。  
  
 グローバル クエリを追加するには、**データセット デザイナー**から**TableAdapter クエリの構成ウィザード**を実行します。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### データセットにグローバル クエリを追加するには  
  
1.  **データセット デザイナー**でデータセットを開きます。  詳細については、「[方法 : データセット デザイナーでデータセットを開く](../Topic/How%20to:%20Open%20a%20Dataset%20in%20the%20Dataset%20Designer.md)」を参照してください。  
  
2.  **ツールボックス**の **\[データセット\]** タブから**データセット デザイナー**の空の領域に、**\[Query\]** をドラッグします。  
  
     [TableAdapter クエリの構成ウィザード](../data-tools/editing-tableadapters.md)が開きます。  
  
3.  使用するクエリの接続を選択します。  一覧から接続を選択するか、または新しい接続を作成できます。  新しい接続を作成する場合、アプリケーション構成ファイルにも接続を保存できます。  詳細については、「[方法: 接続文字列を保存および編集する](../Topic/How%20to:%20Save%20and%20Edit%20Connection%20Strings.md)」を参照してください。  
  
4.  SQL ステートメントを使用するか、またはストアド プロシージャを使用するかを選択します。  
  
5.  使用するストアド プロシージャを選択するか、ウィザードの **\[クエリの種類の選択\]** ページで目的のクエリの種類を選択して **\[次へ\]** をクリックします。  
  
6.  目的のタスクを実行するクエリ \(たとえば、`SELECT COUNT(*) AS CustomerCount FROM Customers`\) を指定します。  
  
    > [!NOTE]
    >  **データセット デザイナー**に直接クエリをドラッグすると、スカラー \(単一\) 値のみを返すメソッドが作成されます。  選択したクエリまたはストアド プロシージャは 1 つ以上の値を返すことができますが、ウィザードで作成したメソッドは単一の値だけを返します。  たとえば、返されたデータの最初の行にある最初の列がクエリから返されます。  
  
7.  ウィザードが完了し、**データセット デザイナー**にクエリが追加されます。  クエリを実行する方法の詳細については、「[方法 : TableAdapter クエリを実行する](../Topic/How%20to:%20Execute%20TableAdapter%20Queries.md)」を参照してください。  
  
## 参照  
 [方法 : TableAdapter を作成する](../data-tools/create-and-configure-tableadapters.md)   
 [方法 : TableAdapter クエリを作成する](../data-tools/how-to-create-tableadapter-queries.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [型指定されたデータセットの作成と編集](../data-tools/creating-and-editing-typed-datasets.md)   
 [データ ソースの概要](../data-tools/add-new-data-sources.md)   
 [方法 : データベース内のデータに接続する](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [方法 : Windows フォーム BindingNavigator コントロールを使用してデータ間を移動する](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)   
 [チュートリアル: Windows フォームでのデータの表示](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)