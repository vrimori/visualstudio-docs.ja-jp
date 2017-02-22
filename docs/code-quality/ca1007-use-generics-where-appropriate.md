---
title: "CA1007: 適切な場所にジェネリックを使用します | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1007"
  - "UseGenericsWhereAppropriate"
helpviewer_keywords: 
  - "CA1007"
  - "UseGenericsWhereAppropriate"
ms.assetid: eab780ea-3b1f-4d32-b15a-5d48da2df46b
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1007: 適切な場所にジェネリックを使用します
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UseGenericsWhereAppropriate|  
|CheckId|CA1007|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## 原因  
 外部から参照可能なメソッドに <xref:System.Object?displayProperty=fullName> 型の参照パラメーターが含まれており、包含アセンブリが [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] を対象としています。  
  
## 規則の説明  
 参照パラメーターは、`ref` \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] では `ByRef`\) キーワードを使用して修正されるパラメーターです。  参照パラメーターに指定される引数の型は、参照パラメーターの型と厳密に一致する必要があります。  参照パラメーターの型から派生した型を使用するには、まずその型をキャストして、参照パラメーターの型の変数に割り当てる必要があります。  ジェネリック メソッドを使用することで、型を最初に参照パラメーターの型にキャストせずに、制約の影響を受けるすべての型をメソッドに渡すことができます。  
  
## 違反の修正方法  
 この規則違反を修正するには、メソッドをジェネリック メソッドに変え、型パラメーターを使用して <xref:System.Object> パラメーターを置き換えます。  
  
## 警告を抑制する状況  
 この規則による警告は抑制しないでください。  
  
## 使用例  
 非ジェネリック メソッドおよびジェネリック メソッドとして実装された汎用スワップ ルーチンを次の例に示します。  非ジェネリック メソッドと比較して、ジェネリック メソッドを使用して文字列をスワップする場合の効率の高さに注目してください。  
  
 [!code-vb[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/VisualBasic/ca1007-use-generics-where-appropriate_1.vb)]
 [!code-cs[FxCop.Design.UseGenerics#1](../code-quality/codesnippet/CSharp/ca1007-use-generics-where-appropriate_1.cs)]  
  
## 関連規則  
 [CA1005: ジェネリック型でパラメーターを使用しすぎないでください](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1010: コレクションは、ジェネリック インターフェイスを実装しなければなりません](../code-quality/ca1010-collections-should-implement-generic-interface.md)  
  
 [CA1000: ジェネリック型の静的メンバーを宣言しません](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: ジェネリック リストを公開しません](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006: ジェネリック型をメンバー シグネチャ内で入れ子にしません](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: ジェネリック メソッドは型パラメーターを指定しなければなりません](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: 汎用イベント ハンドラーのインスタンスを使用します](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
## 参照  
 [ジェネリック](/dotnet/csharp/programming-guide/generics/index)