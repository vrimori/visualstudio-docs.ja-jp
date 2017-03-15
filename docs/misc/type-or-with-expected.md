---
title: "型または &#39;With&#39; が必要です | Microsoft Docs"
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
  - "vbc30988"
  - "bc30988"
helpviewer_keywords: 
  - "BC30988"
ms.assetid: ab9c0cee-9fe4-4764-a3c2-aec16e709d4c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型または &#39;With&#39; が必要です
クラスのインスタンスを宣言するときには、`New` キーワードに続いて、型名または `With` を指定しなければなりません。 たとえば、次の各ステートメントは `client` が `Customer` クラスのインスタンスとなることを宣言しています。 型名 `Customer` が `New` の後に置かれています。  
  
```  
' Dim client As New Customer()  
' The next declaration uses an object initializer.  
Dim client As New Customer() With {.Name = "Litware, Inc."}  
```  
  
 [!INCLUDE[vb_orcas_long](../misc/includes/vb_orcas_long_md.md)] 以降、匿名型のインスタンスとしてオブジェクトを宣言できます。その場合にはデータ型を指定しません。 匿名型の宣言では、キーワード `With` を `New` の後に置きます。  
  
```  
Dim person = New With {.Name ="Mike Nash", .Age = 27}  
```  
  
 **エラー ID:** BC30988  
  
### このエラーを解決するには  
  
-   宣言を変更し、`With` または型名を `New` の後に指定します。  
  
## 参照  
 [Anonymous Types](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types)   
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [NotInBuild: Visual Basic の宣言ステートメント](http://msdn.microsoft.com/ja-jp/81f3c398-f45c-4d95-80bf-aa39d1a0fb30)