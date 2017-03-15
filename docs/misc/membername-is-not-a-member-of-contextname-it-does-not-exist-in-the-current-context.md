---
title: "&#39;&lt;membername&gt;&#39; は &#39;&lt;contextname&gt;&#39; のメンバーではなく、現在のコンテキストに存在しません | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36557"
  - "bc36557"
helpviewer_keywords: 
  - "BC36557"
ms.assetid: d8671f1c-d545-44da-89b3-7d892e01e8be
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;membername&gt;&#39; は &#39;&lt;contextname&gt;&#39; のメンバーではなく、現在のコンテキストに存在しません
匿名型の宣言で、存在しないメンバーの名前がプロパティに割り当てられています。 次の例では、`.Prop1` と `.Prop2` が匿名型のプロパティです。`.Prop3` を `.Prop2` に割り当てようとすると、エラーが発生します。  
  
```vb#  
' Not valid.  
Dim anon1 = New With {.Prop1 = 27, .Prop2 = .Prop3}  
  
' The assignment is valid if the assigned property has been declared   
' and initialized.  
Dim anon2 = New With {.Prop1 = 27, .Prop2 = .Prop1}  
```  
  
 **エラー ID:** BC36657  
  
### このエラーを解決するには  
  
-   割り当てる内容を決定するコードを調べます。 変数名のスペルを間違えている可能性があります。あるいは、割り当てる内容が別のオブジェクトのプロパティである場合には、修飾子が必要になることがあります。  
  
## 参照  
 [Anonymous Types](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [方法 : 匿名型の宣言におけるプロパティ名と型を推論する](../Topic/How%20to:%20Infer%20Property%20Names%20and%20Types%20in%20Anonymous%20Type%20Declarations%20\(Visual%20Basic\).md)