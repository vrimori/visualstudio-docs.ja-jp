---
title: "CA1010: コレクションは、ジェネリック インターフェイスを実装しなければなりません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1010"
  - "CollectionsShouldImplementGenericInterface"
helpviewer_keywords: 
  - "CA1010"
  - "CollectionsShouldImplementGenericInterface"
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# CA1010: コレクションは、ジェネリック インターフェイスを実装しなければなりません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CollectionsShouldImplementGenericInterface|  
|CheckId|CA1010|  
|分類|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## 原因  
 外部から参照可能な型は、<xref:System.Collections.IEnumerable?displayProperty=fullName> インターフェイスを実装していますが、<xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> インターフェイスを実装していません。また、包含アセンブリが [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] を対象としています。  この規則は、<xref:System.Collections.IDictionary?displayProperty=fullName> を実装する型を無視します。  
  
## 規則の説明  
 コレクションの操作性を拡充するために、ジェネリック コレクション インターフェイスの 1 つを実装します。  次に、コレクションを使用して、次のようなジェネリック コレクション型を設定できます。  
  
-   <xref:System.Collections.Generic.List%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>  
  
## 違反の修正方法  
 この規則違反を修正するには、次のジェネリック コレクション インターフェイスの 1 つを実装します。  
  
-   <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.IList%601?displayProperty=fullName>  
  
## 警告を抑制する状況  
 この規則による警告を抑制しても安全ですが、コレクションの用途が限定されます。  
  
## 違反例  
  
### 説明  
 この規則に違反する例として、非ジェネリック `CollectionBase` クラスから派生したクラス \(参照型\) を次に示します。  
  
### コード  
 [!code-cs[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]  
  
### コメント  
 この規則違反を修正するには、ジェネリック インターフェイスを実装するか、`Collection<T>` クラスのように、ジェネリック インターフェイスと非ジェネリック インターフェイスの両方を既に実装している型に基本クラスを変更する必要があります。  
  
## 基本クラスの変更による修正  
  
### 説明  
 コレクションの基本クラスを非ジェネリック `CollectionBase` クラスからジェネリック `Collection<T>` \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] の `Collection(Of T)`\) クラスに変更することによって上記の違反を修正するコード例を次に示します。  
  
### コード  
 [!code-cs[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]  
  
### コメント  
 既にリリースされているクラスの基本クラスを変更することは、既存のコンシューマーに対する互換性に影響すると考えられます。  
  
## インターフェイスの実装による修正  
  
### 説明  
 これらのジェネリック インターフェイス `IEnumerable<T>`、`ICollection<T>`、および `IList<T>` \([!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] の `IEnumerable(Of T)`、`ICollection(Of T)`、および `IList(Of T)`\) の実装によって上記の違反を修正するコード例を次に示します。  
  
### コード  
 [!code-cs[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]  
  
## 関連規則  
 [CA1005: ジェネリック型でパラメーターを使用しすぎないでください](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1000: ジェネリック型の静的メンバーを宣言しません](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: ジェネリック リストを公開しません](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)  
  
 [CA1006: ジェネリック型をメンバー シグネチャ内で入れ子にしません](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: ジェネリック メソッドは型パラメーターを指定しなければなりません](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: 汎用イベント ハンドラーのインスタンスを使用します](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)  
  
 [CA1007: 適切な場所にジェネリックを使用します](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## 参照  
 [ジェネリック](/dotnet/csharp/programming-guide/generics/index)