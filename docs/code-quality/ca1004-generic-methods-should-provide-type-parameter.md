---
title: "CA1004: ジェネリック メソッドは型パラメーターを指定しなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1004"
  - "GenericMethodsShouldProvideTypeParameter"
helpviewer_keywords: 
  - "CA1004"
  - "GenericMethodsShouldProvideTypeParameter"
ms.assetid: 38755f6a-fb45-4bf2-932e-0354ad826499
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1004: ジェネリック メソッドは型パラメーターを指定しなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|GenericMethodsShouldProvideTypeParameter|  
|CheckId|CA1004|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 外部から参照可能なジェネリック メソッドのパラメーター シグネチャに、そのメソッドのすべての型パラメーターに対応する型が含まれていません。  
  
## 規則の説明  
 型引数を明示的に指定するのではなく、メソッドに渡す引数の型によってジェネリック メソッドの型引数を決定する方法が推論されます。  推論を有効にするには、ジェネリック メソッドのパラメーター シグネチャに、そのメソッドの型パラメーターと同じ型のパラメーターが含まれている必要があります。  この場合、型引数を指定する必要がなくなります。  すべての型パラメーターについて推論を使用する場合、ジェネリック インスタンス メソッドを呼び出す構文と、非ジェネリック インスタンス メソッドを呼び出す構文は同じになります。  これにより、ジェネリック メソッドの使用方法が単純化されます。  
  
## 違反の修正方法  
 この規則違反を修正するには、メソッドのすべての型パラメーターについて同じ型がパラメーター シグネチャに含まれるようにデザインを変更します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  理解しやすく使いやすい構文でジェネリック型を指定することで、習得に必要な時間が短縮され、新しいライブラリの採用率が向上します。  
  
## 使用例  
 2 つのジェネリック メソッドを呼び出す構文を次の例に示します。  `InferredTypeArgument` の型引数は推論されます。`NotInferredTypeArgument` の型引数は明示的に指定する必要があります。  
  
 [!code-vb[FxCop.Design.Inference#1](../code-quality/codesnippet/VisualBasic/ca1004-generic-methods-should-provide-type-parameter_1.vb)]
 [!code-cs[FxCop.Design.Inference#1](../code-quality/codesnippet/CSharp/ca1004-generic-methods-should-provide-type-parameter_1.cs)]  
  
## 関連規則  
 [CA1005: ジェネリック型でパラメーターを使用しすぎないでください](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: コレクションは、ジェネリック インターフェイスを実装しなければなりません](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: ジェネリック型の静的メンバーを宣言しません](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: ジェネリック リストを公開しません](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006: ジェネリック型をメンバー シグネチャ内で入れ子にしません](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1003: 汎用イベント ハンドラーのインスタンスを使用します](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007: 適切な場所にジェネリックを使用します](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## 参照  
 [ジェネリック](/dotnet/csharp/programming-guide/generics/index)