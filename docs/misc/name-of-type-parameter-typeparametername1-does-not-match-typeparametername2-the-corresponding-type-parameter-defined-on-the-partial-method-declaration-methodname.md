---
title: "型パラメーターの名前 &#39;&lt;typeparametername1&gt;&#39; は、部分メソッドの宣言 &#39;&lt;methodname&gt;&#39; で定義された、対応する型パラメーター &#39;&lt;typeparametername2&gt;&#39; と一致しません | Microsoft Docs"
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
  - "vbc31443"
  - "bc31443"
helpviewer_keywords: 
  - "BC31443"
ms.assetid: 27c81cc1-325e-4e86-9d00-34f81e928076
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型パラメーターの名前 &#39;&lt;typeparametername1&gt;&#39; は、部分メソッドの宣言 &#39;&lt;methodname&gt;&#39; で定義された、対応する型パラメーター &#39;&lt;typeparametername2&gt;&#39; と一致しません
1 つまたは複数の型パラメーターを含む部分メソッドでは、型パラメーターの名前はメソッドの宣言とメソッドの実装で同じである必要があります。  
  
 たとえば、次の宣言と実装では、このエラーが発生します。  
  
```vb#  
' Definition of the partial method signature with type parameter T. Partial Private Sub OnNameChanged(Of T)() End Sub  
```  
  
```vb#  
'' Implementation of the partial method with type parameter N. 'Private Sub OnNameChanged(Of N)() '    Console.WriteLine("Name was changed to " & Me.Name) 'End Sub  
```  
  
 **エラー ID:** BC31443  
  
### このエラーを解決するには  
  
-   型パラメーターを調べて、一致しない場所を判別します。 必要に応じて名前を変更し、一致させます。  
  
## 参照  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)