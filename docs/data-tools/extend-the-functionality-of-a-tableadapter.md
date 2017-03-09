---
title: "方法 : TableAdapter の機能を拡張する | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
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
  - "データ [Visual Studio], 拡張 (TableAdapters を) "
  - "データ [Visual Studio], TableAdapter"
  - "TableAdapter, 追加 (機能を)"
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 方法 : TableAdapter の機能を拡張する
TableAdapter の機能は、TableAdapter の部分クラス ファイルにコードを追加することによって拡張できます。  
  
 **データセット デザイナー**で TableAdapter が変更されるか、または TableAdapter の構成を変更するウィザードの実行中に何らかの変更が行われると、TableAdapter を定義するコードが再生成されます。  TableAdapter の再生成中にコードが削除されるのを防ぐには、TableAdapter の部分クラス ファイルにコードを追加します。  
  
 部分クラスによって、特定のクラスのコードを複数の物理ファイルに分割できます。  詳細については、「[Partial](/dotnet/visual-basic/language-reference/modifiers/partial)」または「[partial \(型\)](/dotnet/csharp/language-reference/keywords/partial-type)」を参照してください。  
  
## コード内の TableAdapter の場所の特定  
 TableAdapter はデータセット デザイナーでデザインされますが、生成される TableAdapter のクラスは、<xref:System.Data.DataSet> の入れ子にされたクラスとして生成されるわけではありません。  TableAdapter は、TableAdapter に関連付けられたデータセットの名前に基づいた名前空間にあります。  たとえば、アプリケーションに `HRDataSet` というデータセットがある場合、TableAdapter は `HRDataSetTableAdapters` という名前空間にあります。  名前付け規則は *DatasetName* \+ `TableAdapters` というパターンになります。  
  
 次の例では、`NorthwindDataSet` を含むプロジェクトに `CustomersTableAdapter` という TableAdapter があると仮定しています。  
  
#### TableAdapter の部分クラスを作成するには  
  
1.  **\[プロジェクト\]** メニューの **\[クラスの追加\]** をクリックして、新規クラスをプロジェクトに追加します。  
  
2.  クラスに `CustomersTableAdapterExtended` という名前を付けます。  
  
3.  **\[追加\]** をクリックします。  
  
4.  プロジェクトの適切な名前空間と部分クラスの名前でコードを置き換えます。  次に例を示します。  
  
     [!CODE [VbRaddataTableAdapters#2](../CodeSnippet/VS_Snippets_VBCSharp/VbRaddataTableAdapters#2)]  
  
## 参照  
 [TableAdapter の概要](../data-tools/tableadapter-overview.md)   
 [方法 : TableAdapter を作成する](../data-tools/create-and-configure-tableadapters.md)   
 [方法 : TableAdapter クエリを作成する](../data-tools/how-to-create-tableadapter-queries.md)   
 [方法 : データセットの機能を拡張する](../Topic/How%20to:%20Extend%20the%20Functionality%20of%20a%20Dataset.md)   
 [データに関するチュートリアル](../Topic/Data%20Walkthroughs.md)   
 [Visual Studio でのデータへの Windows フォーム コントロールのバインド](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Visual Studio のデータ アプリケーションの概要](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Visual Studio でのデータへの接続](../data-tools/connecting-to-data-in-visual-studio.md)   
 [アプリケーションでデータを受け取る準備](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [アプリケーションへのデータのフェッチ](../data-tools/fetching-data-into-your-application.md)   
 [Visual Studio でのデータへのコントロールのバインド](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [アプリケーションでのデータ編集](../data-tools/editing-data-in-your-application.md)   
 [データの検証](../Topic/Validating%20Data.md)   
 [データの保存](../data-tools/saving-data.md)