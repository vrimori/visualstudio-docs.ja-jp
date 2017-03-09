---
title: "型パラメーター制約 &#39;&lt;typeparameter1&gt;&#39; から取得された間接的な制約 &#39;&lt;constraint1&gt;&#39; は、制約 &#39;&lt;constraint2&gt;&#39; と競合しています | Microsoft Docs"
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
  - "bc32111"
  - "vbc32111"
helpviewer_keywords: 
  - "BC32111"
ms.assetid: b03b5840-5318-4844-b2da-1bca4c28d097
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型パラメーター制約 &#39;&lt;typeparameter1&gt;&#39; から取得された間接的な制約 &#39;&lt;constraint1&gt;&#39; は、制約 &#39;&lt;constraint2&gt;&#39; と競合しています
直接的な制約と間接的な制約の組み合わせにより、競合する制約を備えたジェネリック型が宣言されています。  
  
 次のステートメントでは、このエラーが生成される可能性があります。  
  
 `Public Class testClass(Of t1 As {t2, Class}, t2 As Structure)`  
  
 間接的な制約 `Structure` と直接的な制約 `Class` により、型パラメーター `t1` について競合が発生しています。`Structure` 制約は対応する型引数に値型を要求し、`Class` 制約は参照型を要求するからです。  
  
 **エラー ID:** BC32111  
  
### このエラーを解決するには  
  
-   制約の競合が生じないように、型パラメーターの制約を変更します。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)   
 [構造体 \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [クラス \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)