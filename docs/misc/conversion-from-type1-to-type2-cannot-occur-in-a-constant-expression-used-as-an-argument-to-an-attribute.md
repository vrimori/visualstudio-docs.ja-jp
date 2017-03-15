---
title: "属性に対する引数として使用される定数式で、&#39;&lt;type1&gt;&#39; から &#39;&lt;type2&gt;&#39; に変換することはできません | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30934"
  - "vbc30934"
helpviewer_keywords: 
  - "BC30934"
ms.assetid: 120e05f9-1d0e-4800-b05c-a8373e286b9b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 属性に対する引数として使用される定数式で、&#39;&lt;type1&gt;&#39; から &#39;&lt;type2&gt;&#39; に変換することはできません
属性引数に使用される式が、対応する属性パラメーターのものとは異なるデータ型に評価されます。[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では、属性引数に必要な型変換を実施できません。  
  
 属性はその属性に適用される要素のメタデータを提供し、コンパイラはコンパイル時にそのすべてのメタデータを構築できる必要があります。 このため、すべての属性がコンパイル時に定数となる値を使用する必要があり、したがって、すべての属性引数がコンパイル時の定数値に評価される必要があります。  
  
 一部の型変換では、コンパイル時に一定となる値を生成できないことがあります。 たとえば、`String` を `Double` に変換するか `Date` に変換するかは、実行時のロケール設定によって異なります。 これ以外に、派生型の配列を `Object` の配列にするなどの変換でも、さまざまな問題が発生して、コンパイラで属性引数を変換できないことがあります。  
  
 **エラー ID:** BC30934  
  
### このエラーを解決するには  
  
-   属性で定義されているとおりに、対応するパラメーターと同じデータ型に評価される式を使用します。  
  
## 参照  
 [ビルド内にありません: Visual Basic における属性](http://msdn.microsoft.com/ja-jp/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [ビルド内にありません: 属性の適用](http://msdn.microsoft.com/ja-jp/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Const Statement](/dotnet/visual-basic/language-reference/statements/const-statement)   
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)