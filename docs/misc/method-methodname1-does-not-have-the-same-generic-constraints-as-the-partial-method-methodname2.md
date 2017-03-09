---
title: "メソッド &#39;&lt;methodname1&gt;&#39; に、部分メソッド &#39;&lt;methodname2&gt;&#39; と同じジェネリック制約がありません。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc31438"
  - "vbc31438"
helpviewer_keywords: 
  - "BC31438"
ms.assetid: ea092f0c-661b-49db-80c1-76401fc8bc0b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# メソッド &#39;&lt;methodname1&gt;&#39; に、部分メソッド &#39;&lt;methodname2&gt;&#39; と同じジェネリック制約がありません。
部分メソッドの宣言内の制約とは異なるジェネリック制約を持つ部分メソッドの実装を定義しています。 このエラーが発生するコード例を次に示します。  
  
```vb#  
Partial Class Class1 Partial Private Sub Test(Of T As Class)(ByVal arg As T) End Sub End Class Partial Class Class1 '' The error occurs here, for Test. 'Private Sub Test(Of T As Structure)(ByVal arg As T) 'End Sub End Class  
```  
  
 **エラー ID:** BC31438  
  
## 参照  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)