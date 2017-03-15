---
title: "制約 &#39;&lt;constraint1&gt;&#39; は、型パラメーター &#39;&lt;typeparametername&gt;&#39; に対して既に指定されている制約 &#39;&lt;constraint2&gt;&#39; と競合しています | Microsoft Docs"
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
  - "vbc32119"
  - "bc32119"
helpviewer_keywords: 
  - "BC32119"
ms.assetid: 30e6778d-5c2b-4f2d-a136-4e66fa9fbe4d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 制約 &#39;&lt;constraint1&gt;&#39; は、型パラメーター &#39;&lt;typeparametername&gt;&#39; に対して既に指定されている制約 &#39;&lt;constraint2&gt;&#39; と競合しています
ジェネリック型が、型パラメーターで競合する制約を使用して宣言されています。  
  
 このエラーは次のようなステートメントで発生することがあります。  
  
 `Public Class testClass(Of t As {Structure, Class })`  
  
 制約 `Structure` と制約 `Class` により、型パラメーター `t` について競合が発生しています。`Structure` 制約は対応する型引数に値型を要求するのに対し、`Class` 制約は参照型を要求するためです。  
  
 **エラー ID:** BC32119  
  
### このエラーを解決するには  
  
-   競合が生じないように、型パラメーターの制約を変更します。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [Structure \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [Class \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)