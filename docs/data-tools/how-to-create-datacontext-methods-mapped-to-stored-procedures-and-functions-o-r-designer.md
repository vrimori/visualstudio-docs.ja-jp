---
title: "How to: Create DataContext Methods Mapped to Stored Procedures and Functions (O/R Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Create DataContext Methods Mapped to Stored Procedures and Functions (O/R Designer)
ストアド プロシージャと関数は、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]に <xref:System.Data.Linq.DataContext> のメソッドとして追加できます。メソッドを呼び出して必要なパラメーターを渡すと、データベースでストアド プロシージャまたは関数が実行され、<xref:System.Data.Linq.DataContext> メソッドの戻り値の型のデータが返されます。<xref:System.Data.Linq.DataContext> メソッドの詳細については、「[DataContext Methods \(O\/R Designer\)](../data-tools/datacontext-methods-o-r-designer.md)」を参照してください。  
  
> [!NOTE]
>  ストアド プロシージャを使用して、エンティティ クラスからデータベースに変更が保存されたときに挿入、更新、および削除を実行する既定の [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] ランタイムの動作をオーバーライドすることもできます。詳細については、「[How to: Assign Stored Procedures to Perform Updates, Inserts, and Deletes \(O\/R Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)」を参照してください。  
  
## DataContext メソッドの作成  
 **サーバー エクスプローラー**またはデータベース エクスプローラーから [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]にストアド プロシージャをドラッグすることで、<xref:System.Data.Linq.DataContext> のメソッドを作成できます。  
  
> [!NOTE]
>  生成される <xref:System.Data.Linq.DataContext> メソッドの戻り値の型は、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]でストアド プロシージャまたは関数をドロップする場所によって異なります。既存のエンティティ クラスに項目を直接ドロップすると、そのエンティティ クラスを戻り値の型とする <xref:System.Data.Linq.DataContext> メソッドが作成されます。[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]の空の領域に項目をドロップすると、自動生成された型を返す <xref:System.Data.Linq.DataContext> メソッドが作成されます。<xref:System.Data.Linq.DataContext> メソッドをメソッド ペインに追加した後に、その戻り値の型を変更できます。<xref:System.Data.Linq.DataContext> メソッドの戻り値の型を確認または変更するには、**\[プロパティ\]** ウィンドウでメソッドを選択し、**\[Return Type\]** プロパティを調べます。詳細については、「[How to: Change the Return Type of a DataContext Method \(O\/R Designer\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)」を参照してください。  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### 自動生成された型を返す DataContext メソッドを作成するには  
  
1.  **サーバー エクスプローラー**または**データベース エクスプローラー**で、作業中のデータベースの **\[ストアド プロシージャ\]** ノードを展開します。  
  
2.  目的のストアド プロシージャを探し、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]の空の領域にドラッグします。  
  
     自動生成された戻り値の型で <xref:System.Data.Linq.DataContext> メソッドが作成され、**\[メソッド\]** ペインに表示されます。  
  
#### エンティティ クラスを戻り値の型とする DataContext メソッドを作成するには  
  
1.  **サーバー エクスプローラー**または**データベース エクスプローラー**で、作業中のデータベースの **\[ストアド プロシージャ\]** ノードを展開します。  
  
2.  目的のストアド プロシージャを探し、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]の既存のエンティティ クラスにドラッグします。  
  
     選択したエンティティ クラスを戻り値の型として <xref:System.Data.Linq.DataContext> メソッドが作成され、**\[メソッド\]** ペインに表示されます。  
  
> [!NOTE]
>  既存の <xref:System.Data.Linq.DataContext> メソッドの戻り値の型を変更する方法については、「[How to: Change the Return Type of a DataContext Method \(O\/R Designer\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)」を参照してください。  
  
## 参照  
 [Object Relational Designer \(O\/R Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [DataContext Methods \(O\/R Designer\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Introduction to LINQ in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)   
 [方法 : C\# で LINQ クエリを作成する](../Topic/How%20to:%20Write%20LINQ%20Queries%20in%20C%23.md)