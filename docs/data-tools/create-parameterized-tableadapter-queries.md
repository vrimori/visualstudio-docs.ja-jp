---
title: "方法 : パラメーター付きの TableAdapter クエリを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
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
  - "データ [Visual Studio], 検索 (データを)"
  - "データ [Visual Studio], TableAdapter"
  - "クエリ [Visual Studio], 作成"
  - "クエリ [Visual Studio], TableAdapter"
  - "TableAdapter, パラメーター クエリ"
  - "TableAdapter, 検索 (データを)"
ms.assetid: 104d1d19-b5a9-4071-b81e-1b3af08e9c7b
caps.latest.revision: 20
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 方法 : パラメーター付きの TableAdapter クエリを作成する
パラメーター クエリは、クエリ内の WHERE 句の条件を満たすデータを返します。  たとえば、顧客リストをパラメーター化して、顧客のリストを戻す SQL ステートメントに `WHERE City = @City` を追加することで、特定の都市の顧客のみが表示されるようにできます。  
  
 パラメーター化された TableAdapter クエリは、[データセット デザイナー](../data-tools/creating-and-editing-typed-datasets.md)で作成するか、または Windows アプリケーションでデータ バインド フォームを作成するときに **\[データ\]** メニューの **\[データ ソースのパラメーター化\]** を使用して作成します。  **\[データ ソースのパラメーター化\]** コマンドによって、パラメーター値を入力してクエリを実行するためのコントロールもフォームに作成されます。  詳細については、「[ダイアログ ボックス](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md)」を参照してください。  
  
> [!NOTE]
>  パラメーター クエリを作成するときには、コーディングで対象とするデータベースに固有のパラメーター表記を使用します。  たとえば、Access データ ソースと OleDb データ ソースは疑問符 "?" を使用してパラメーターを表すため、WHERE 句は `WHERE City = ?` のようになります。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## パラメーター化された TableAdapter クエリの作成  
  
#### データセット デザイナーでパラメーター クエリを作成するには  
  
-   新しい TableAdapter を作成し、目的のパラメーターを含む WHERE 句を SQL ステートメントに追加します。  詳細については、「[方法 : TableAdapter を作成する](../data-tools/create-and-configure-tableadapters.md)」を参照してください。  
  
     または  
  
-   既存の TableAdapter にクエリを追加し、目的のパラメーターを含む WHERE 句を SQL ステートメントに追加します。  詳細については、「[方法 : TableAdapter クエリを作成する](../data-tools/how-to-create-tableadapter-queries.md)」を参照してください。  
  
#### データ バインド フォームの設計時にパラメーター クエリを作成するには  
  
1.  フォーム上の既にデータセットにバインドされているコントロールを選択します。  詳細については、「[Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)」を参照してください。  
  
2.  **\[データ\]** メニューの **\[クエリの追加\]** をクリックします。  
  
3.  **\[検索条件ビルダー\]** ダイアログ ボックスの設定を完了し、目的のパラメーターを含む WHERE 句を SQL ステートメントに追加します。  詳細については、「[ダイアログ ボックス](../Topic/Search%20Criteria%20Builder%20Dialog%20Box.md)」を参照してください。  
  
## 参照  
 [TableAdapter](../Topic/TableAdapters.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)   
 [データに関するチュートリアル](../Topic/Data%20Walkthroughs.md)