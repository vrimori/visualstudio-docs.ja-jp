---
title: "DataContext Methods (O/R Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 5
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DataContext Methods (O/R Designer)
<xref:System.Data.Linq.DataContext> メソッド \([Object Relational Designer \(O\/R Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md) のコンテキスト\) は、データベース内のストアド プロシージャおよび関数を実行する <xref:System.Data.Linq.DataContext> クラスのメソッドです。  
  
 <xref:System.Data.Linq.DataContext> クラスは、SQL Server データベースと、そのデータベースにマップされる [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] エンティティ クラスの間のパイプ役として機能する [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] クラスです。<xref:System.Data.Linq.DataContext> クラスには、接続文字列の情報と、データベースへの接続およびデータベース内のデータの操作を行うメソッドが含まれています。既定では、<xref:System.Data.Linq.DataContext> クラスに、呼び出すことのできるいくつかのメソッドが含まれます。たとえば、更新されたデータを [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] クラスからデータベースに送信する <xref:System.Data.Linq.DataContext.SubmitChanges%2A> メソッドなどです。また、ストアド プロシージャおよび関数にマップされる追加の <xref:System.Data.Linq.DataContext> メソッドを作成することもできます。つまり、これらのカスタム メソッドを呼び出すと、<xref:System.Data.Linq.DataContext> メソッドのマップ先となっているデータベース内のストアド プロシージャまたは関数が実行されます。メソッドを追加して任意のクラスを拡張するのと同じように、<xref:System.Data.Linq.DataContext> クラスに新しいメソッドを追加できます。ただし、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]のコンテキストにおける <xref:System.Data.Linq.DataContext> メソッドの説明では、ストアド プロシージャおよび関数にマップされる <xref:System.Data.Linq.DataContext> メソッドを説明の対象としています。  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] では、ストアド プロシージャと関数は同じ方法で処理され、両方とも同じ <xref:System.Data.Linq.StoredProcedureAttribute> を使用してエンティティ クラスにマップされます。[!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] のコンテキストでは、ストアド プロシージャにマップされる <xref:System.Data.Linq.DataContext> メソッドは、関数にマップされるメソッドと同じです。  
  
## メソッド ペイン  
 ストアド プロシージャおよび関数にマップされる <xref:System.Data.Linq.DataContext> メソッドは、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]のメソッド ペインに表示されます。メソッド ペインは、**エンティティ** ペイン \(メインのデザイン サーフェイス\) の横に表示されているペインです。メソッド ペインには、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]を使用して作成されたすべての <xref:System.Data.Linq.DataContext> メソッドが表示されます。既定ではメソッド ペインは空です。<xref:System.Data.Linq.DataContext> メソッドを作成し、メソッド ペインにデータを設定するには、**サーバー エクスプローラー**または**データベース エクスプローラー**から、ストアド プロシージャまたは関数を [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]にドラッグします。詳細については、「[How to: Create DataContext Methods Mapped to Stored Procedures and Functions \(O\/R Designer\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)」を参照してください。  
  
> [!NOTE]
>  メソッド ペインを開いたり閉じたりするには、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]を右クリックし、**\[メソッド ペインの非表示\]** または **\[メソッド ペインの表示\]** をクリックするか、Ctrl \+ 1 のショートカット キーを使用します。  
  
## 2 種類の DataContext メソッド  
 DataContext メソッドは、データベース内のストアド プロシージャおよび関数にマップされるメソッドです。DataContext メソッドは、[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]のメソッド ペインで作成および追加できます。<xref:System.Data.Linq.DataContext> メソッドには、1 つ以上の結果セットを返すものと結果セットを返さないものの 2 種類があります。  
  
-   1 つ以上の結果セットを返す <xref:System.Data.Linq.DataContext> メソッド  
  
     この種類の <xref:System.Data.Linq.DataContext> メソッドは、アプリケーションでデータベース内のストアド プロシージャおよび関数を実行し、結果を返すことだけが必要な場合に作成します。詳細については、「[How to: Create DataContext Methods Mapped to Stored Procedures and Functions \(O\/R Designer\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)」、「<xref:System.Data.Linq.ISingleResult%271>」、および「<xref:System.Data.Linq.IMultipleResults>」を参照してください。  
  
-   結果セットを返さない <xref:System.Data.Linq.DataContext> メソッド \(特定のエンティティ クラスの挿入、更新、削除など\)  
  
     この種類の <xref:System.Data.Linq.DataContext> メソッドは、エンティティ クラスとデータベース間で変更されたデータを保存するために、既定の [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] の動作を使用するのではなく、アプリケーションでストアド プロシージャを実行する必要がある場合に作成します。詳細については、「[How to: Assign Stored Procedures to Perform Updates, Inserts, and Deletes \(O\/R Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)」を参照してください。  
  
## DataContext メソッドの戻り値の型  
 **サーバー エクスプローラー**または**データベース エクスプローラー**から [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]にストアド プロシージャまたは関数をドラッグする場合、生成される <xref:System.Data.Linq.DataContext> メソッドの戻り値の型は、項目をドロップする場所によって異なります。既存のエンティティ クラスに項目を直接ドロップすると、そのエンティティ クラスを戻り値の型とする <xref:System.Data.Linq.DataContext> メソッドが作成されます。[!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]の空の領域 \(任意のペイン\) に項目をドロップすると、自動生成された型を返す <xref:System.Data.Linq.DataContext> メソッドが作成されます。作成される自動生成の型は、ストアド プロシージャ名または関数名に一致する名前と、そのストアド プロシージャまたは関数によって返される各フィールドにマップされるプロパティを持ちます。  
  
> [!NOTE]
>  <xref:System.Data.Linq.DataContext> メソッドをメソッド ペインに追加した後に、その戻り値の型を変更できます。<xref:System.Data.Linq.DataContext> メソッドの戻り値の型を確認または変更するには、**\[プロパティ\]** ウィンドウでメソッドを選択し、**\[Return Type\]** プロパティを調べます。詳細については、「[How to: Change the Return Type of a DataContext Method \(O\/R Designer\)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md)」を参照してください。  
  
 データベースから O\/R デザイナー画面にドラッグしたオブジェクトには、データベース内のオブジェクトの名前に基づいて自動的に名前が付けられます。同じオブジェクトを複数回ドラッグすると、新しい名前の末尾に名前を区別する番号が付けられます。データベース オブジェクト名にスペースや Visual Basic または C\# でサポートされない文字が含まれている場合、そのスペースまたは無効な文字はアンダースコアに置き換えられます。  
  
## 参照  
 [Object Relational Designer \(O\/R Designer\)](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Stored Procedures](../Topic/Stored%20Procedures.md)   
 [How to: Create DataContext Methods Mapped to Stored Procedures and Functions \(O\/R Designer\)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [How to: Assign Stored Procedures to Perform Updates, Inserts, and Deletes \(O\/R Designer\)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Walkthrough: Customizing the Insert, Update, and Delete Behavior of Entity Classes](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [Walkthrough: Creating LINQ to SQL Classes \(O\/R Designer\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)