---
title: "How to: Change the Return Type of a DataContext Method (O/R Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Change the Return Type of a DataContext Method (O/R Designer)
ストアド プロシージャまたは関数に基づいて作成された <xref:System.Data.Linq.DataContext> メソッドの戻り値の型は、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]でストアド プロシージャまたは関数をドロップした場所に応じて異なります。既存のエンティティ クラスに項目を直接ドロップすると、そのエンティティ クラスを戻り値の型とする <xref:System.Data.Linq.DataContext> メソッドが作成されます \(ストアド プロシージャまたは関数によって返されるデータのスキーマがエンティティ クラスの形状と一致する場合\)。[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]の空の領域に項目をドロップすると、自動生成された型を返す <xref:System.Data.Linq.DataContext> メソッドが作成されます。<xref:System.Data.Linq.DataContext> メソッドをメソッド ペインに追加した後に、その戻り値の型を変更できます。<xref:System.Data.Linq.DataContext> メソッドの戻り値の型を確認または変更するには、**\[プロパティ\]** ウィンドウでメソッドを選択し、**\[Return Type\]** プロパティをクリックします。  
  
> [!NOTE]
>  **\[プロパティ\]** ウィンドウを使用しても、戻り値の型がエンティティ クラスに設定されている <xref:System.Data.Linq.DataContext> メソッドは、自動生成型を返すようには変更できません。自動生成型を返すように <xref:System.Data.Linq.DataContext> メソッドを戻すには、元のデータベース オブジェクトをもう一度 O\/R デザイナーにドラッグする必要があります。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### DataContext メソッドの戻り値の型を、自動生成型からエンティティ クラスに変更するには  
  
1.  メソッド ペインで <xref:System.Data.Linq.DataContext> メソッドを選択します。  
  
2.  **\[プロパティ\]** ウィンドウの **\[Return Type\]** を選択し、**\[Return Type\]** の一覧で使用可能なエンティティ クラスを選択します。目的のエンティティ クラスが一覧にない場合は、そのエンティティ クラスを追加するか、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]で作成して一覧に追加します。  
  
3.  .dbml ファイルを保存します。  
  
### DataContext メソッドの戻り値の型を、エンティティ クラスから自動生成型に変更するには  
  
1.  メソッド ペインで <xref:System.Data.Linq.DataContext> メソッドを選択し、削除します。  
  
2.  **サーバー エクスプローラー**または**データベース エクスプローラー**から、データベース オブジェクトを O\/R デザイナーの空の領域にドラッグします。  
  
3.  .dbml ファイルを保存します。  
  
## 参照  
 [Object Relational Designer \(O\/R Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [DataContext Methods \(O\/R Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [How to: Create DataContext Methods Mapped to Stored Procedures and Functions \(O\/R Designer\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)