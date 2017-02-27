---
title: "CA1006: ジェネリック型をメンバー シグネチャ内で入れ子にしません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotNestGenericTypesInMemberSignatures"
  - "CA1006"
helpviewer_keywords: 
  - "CA1006"
  - "DoNotNestGenericTypesInMemberSignatures"
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 17
---
# CA1006: ジェネリック型をメンバー シグネチャ内で入れ子にしません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotNestGenericTypesInMemberSignatures|  
|CheckId|CA1006|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 外部から参照可能なメンバーが、入れ子にされた型引数を含むシグネチャを持っています。  
  
## 規則の説明  
 入れ子にされた型引数は、ジェネリック型の型引数でもあります。  入れ子にされた型引数を含むシグネチャを持つメンバーを呼び出すには、ユーザーが 1 つのジェネリック型をインスタンス化し、別のジェネリック型のコンストラクターにこの型を渡す必要があります。  複雑な手順と構文が必要となるため、これは避けるようにしてください。  
  
## 違反の修正方法  
 この規則違反を修正するには、デザインを変更して、入れ子にされた型引数を削除します。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  理解しやすく使いやすい構文でジェネリック型を指定することで、習得に必要な時間が短縮され、新しいライブラリの採用率が向上します。  
  
## 使用例  
 この規則に違反するメソッドと、違反するメソッドを呼び出すために必要な構文を次の例に示します。  
  
 [!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
 [!code-cs[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]  
  
## 関連規則  
 [CA1005: ジェネリック型でパラメーターを使用しすぎないでください](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: コレクションは、ジェネリック インターフェイスを実装しなければなりません](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: ジェネリック型の静的メンバーを宣言しません](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: ジェネリック リストを公開しません](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1004: ジェネリック メソッドは型パラメーターを指定しなければなりません](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: 汎用イベント ハンドラーのインスタンスを使用します](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007: 適切な場所にジェネリックを使用します](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## 参照  
 [ジェネリック](/dotnet/csharp/programming-guide/generics/index)