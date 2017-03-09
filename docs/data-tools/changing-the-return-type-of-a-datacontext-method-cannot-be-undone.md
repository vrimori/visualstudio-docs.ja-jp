---
title: "Changing the return type of a DataContext method cannot be undone | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 76b161fc-5075-4192-8d94-f15b02e199e9
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Changing the return type of a DataContext method cannot be undone
DataContext メソッドの戻り値の型を変更すると、元に戻せなくなります。自動生成された型に戻すには、項目をサーバー エクスプローラー\/データベース エクスプローラーから O\/R デザイナーにもう一度ドラッグする必要があります。戻り値の型を変更してもよろしいですか?  
  
 <xref:System.Data.Linq.DataContext> メソッドの戻り値の型は、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]で項目をドロップする場所によって異なります。既存のエンティティ クラスに項目を直接ドロップすると、そのエンティティ クラスを戻り値の型とする <xref:System.Data.Linq.DataContext> メソッドが作成されます。[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]の空の領域に項目をドロップすると、自動生成された型を返す <xref:System.Data.Linq.DataContext> メソッドが作成されます。<xref:System.Data.Linq.DataContext> メソッドをメソッド ペインに追加した後に、その戻り値の型を変更できます。<xref:System.Data.Linq.DataContext> メソッドの戻り値の型を確認または変更するには、**\[プロパティ\]** ウィンドウでメソッドを選択し、**\[Return Type\]** プロパティをクリックします。  
  
### DataContext の戻り値の型を変更するには  
  
-   **\[はい\]** をクリックします。  
  
### メッセージ ボックスを終了し、現在の戻り値の型を維持するには  
  
-   **\[いいえ\]** をクリックします。  
  
### 戻り値の型を変更した後で、元の戻り値の型に戻すには  
  
1.  [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]で <xref:System.Data.Linq.DataContext> メソッドを選択し、削除します。  
  
2.  **サーバー エクスプローラー**またはデータベース エクスプローラーで項目を探し、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]にドラッグします。  
  
     元の既定の戻り値の型で <xref:System.Data.Linq.DataContext> メソッドが作成されます。  
  
## 参照  
 [Object Relational Designer \(O\/R Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext Methods \(O\/R Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [How to: Create DataContext Methods Mapped to Stored Procedures and Functions \(O\/R Designer\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)