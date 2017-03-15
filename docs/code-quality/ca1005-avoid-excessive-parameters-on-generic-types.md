---
title: "CA1005: ジェネリック型でパラメーターを使用しすぎないでください | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AvoidExcessiveParametersOnGenericTypes"
  - "CA1005"
helpviewer_keywords: 
  - "AvoidExcessiveParametersOnGenericTypes"
  - "CA1005"
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1005: ジェネリック型でパラメーターを使用しすぎないでください
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidExcessiveParametersOnGenericTypes|  
|CheckId|CA1005|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 外部から参照可能なジェネリック型に、3 つ以上の型パラメーターがあります。  
  
## 規則の説明  
 ジェネリック型に含まれる型パラメーターが増えれば増えるほど、それぞれの型パラメーターが表す意味を調べることや覚えることが難しくなります。  通常、`List<T>` のように型パラメーターが 1 つの場合や、`Dictionary<TKey, TValue>` のように型パラメーターが 2 つの場合、意味は明確です。  型パラメーターが 3 つ以上になると、ほとんどのユーザーには意味を把握することが困難になります \(たとえば、C\# では `TooManyTypeParameters<T, K, V>`、[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では `TooManyTypeParameters(Of T, K, V)` のような場合\)。  
  
## 違反の修正方法  
 この規則違反を修正するには、3 つ以上の型パラメーターを使用しないようにデザインを変更します。  
  
## 警告を抑制する状況  
 デザインで 3 つ以上の型パラメーターが絶対に必要な場合を除き、この規則による警告を抑制しないでください。  理解しやすく使いやすい構文でジェネリック型を指定することで、習得に必要な時間が短縮され、新しいライブラリの採用率が向上します。  
  
## 関連規則  
 [CA1010: コレクションは、ジェネリック インターフェイスを実装しなければなりません](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: ジェネリック型の静的メンバーを宣言しません](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: ジェネリック リストを公開しません](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006: ジェネリック型をメンバー シグネチャ内で入れ子にしません](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: ジェネリック メソッドは型パラメーターを指定しなければなりません](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: 汎用イベント ハンドラーのインスタンスを使用します](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007: 適切な場所にジェネリックを使用します](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## 参照  
 [ジェネリック](/dotnet/csharp/programming-guide/generics/index)