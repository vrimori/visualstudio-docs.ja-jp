---
title: "CA1000: ジェネリック型の静的メンバーを宣言しません | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1000"
  - "DoNotDeclareStaticMembersOnGenericTypes"
helpviewer_keywords: 
  - "CA1000"
  - "DoNotDeclareStaticMembersOnGenericTypes"
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1000: ジェネリック型の静的メンバーを宣言しません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotDeclareStaticMembersOnGenericTypes|  
|CheckId|CA1000|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 外部から参照可能なジェネリック型に、`static` \(Visual Basic では `Shared`\) メンバーが含まれています。  
  
## 規則の説明  
 ジェネリック型の `static` メンバーを呼び出すときには、その型の型引数も指定する必要があります。  推論をサポートしないジェネリック インスタンス メンバーを呼び出すときには、そのメンバーに型引数を指定する必要があります。  この 2 つの場合で、型引数を指定するときに使用される構文は異なりますが、混同される可能性があります。次に呼び出しの例を示します。  
  
```vb  
' Shared method in a generic type.  
GenericType(Of Integer).SharedMethod()  
  
' Generic instance method that does not support inference.  
someObject.GenericMethod(Of Integer)()  
```  
  
```c#  
// Static method in a generic type.  
GenericType<int>.StaticMethod();  
  
// Generic instance method that does not support inference.  
someObject.GenericMethod<int>();  
```  
  
 一般的に、メンバーが呼び出されたときに型引数を指定する必要がないように、前者の宣言はどちらも避ける必要があります。  その結果、ジェネリック型のメンバーを呼び出す構文がジェネリック型以外の構文と同じになります。  詳細については、「[CA1004: ジェネリック メソッドは型パラメーターを指定しなければなりません](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)」を参照してください。  
  
## 違反の修正方法  
 このルールの違反を修正するには、静的メンバーを削除するか、インスタンス メンバーに変更します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  理解しやすく使いやすい構文でジェネリック型を指定することで、習得に必要な時間が短縮され、新しいライブラリの採用率が向上します。  
  
## 関連規則  
 [CA1005: ジェネリック型でパラメーターを使用しすぎないでください](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: コレクションは、ジェネリック インターフェイスを実装しなければなりません](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1002: ジェネリック リストを公開しません](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006: ジェネリック型をメンバー シグネチャ内で入れ子にしません](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: ジェネリック メソッドは型パラメーターを指定しなければなりません](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: 汎用イベント ハンドラーのインスタンスを使用します](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007: 適切な場所にジェネリックを使用します](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## 参照  
 [ジェネリック](/dotnet/csharp/programming-guide/generics/index)