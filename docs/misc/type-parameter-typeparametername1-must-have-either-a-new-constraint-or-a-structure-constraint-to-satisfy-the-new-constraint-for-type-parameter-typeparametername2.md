---
title: "型パラメーター &#39;&lt;typeparametername1&gt;&#39; には、型パラメーター &#39;&lt;typeparametername2&gt;&#39; の &#39;New&#39; 制約を満たすために &#39;New&#39; 制約または &#39;Structure&#39; 制約が必要です | Microsoft Docs"
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
  - "vbc32084"
  - "BC32084"
helpviewer_keywords: 
  - "BC32084"
ms.assetid: a7ff58d3-8c67-40e4-9fd8-92cc00524c22
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 型パラメーター &#39;&lt;typeparametername1&gt;&#39; には、型パラメーター &#39;&lt;typeparametername2&gt;&#39; の &#39;New&#39; 制約を満たすために &#39;New&#39; 制約または &#39;Structure&#39; 制約が必要です
ステートメントで、`New` 制約を満たすために制約されていない型パラメーターを渡すジェネリック型を構築します。  
  
 `New` 制約は、その型パラメーターに渡される型引数が、そこからオブジェクトを作成するコードにアクセス可能なパラメーターのないコンストラクターを公開する必要があることを意味します。 すべての値型にパラメーターのないコンストラクターがありますが、すべての参照型にあるわけではありません。 そのため、`Structure` 制約は `New` 制約を満たしていますが、`Class` 制約や、クラスまたはインターフェイスの名前はこの制約を満たしていません。  
  
 次のステートメントでは、このエラーが生成される可能性があります。  
  
```  
Public Class c1(Of t As New) End Class Public Class c2(Of u) Public testObject As New c1(Of u) End Class  
```  
  
 クラス `c2` が `c1` からオブジェクトを作成する場合、型パラメーター `u` は型パラメーター `t` の `New` 制約を満たしていません。  
  
 **エラー ID:** BC32084  
  
### このエラーを解決するには  
  
-   ジェネリック型に渡される型パラメーターが `Structure` または `New` の制約を満たすことができる場合は、その定義に適切な制約を追加します。  
  
    ```  
    Public Class c2(Of u As Structure)  
    ```  
  
-   型パラメーターが `Structure` または `New` の制約を満たすことができない場合は、ジェネリック型にこれを渡しません。 型引数として他のものを渡す必要があります。  
  
## 参照  
 [Visual Basic におけるジェネリック型](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [New Operator](/dotnet/visual-basic/language-reference/operators/new-operator)   
 [構造体 \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/263ce115-ac36-4c05-8cb7-0e0eead5c6d0)   
 [クラス \(Visual Basic\)](http://msdn.microsoft.com/ja-jp/0777c6e6-46bc-451b-ad70-57b49d4ef4f7)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)