---
title: "Ca 1010: コレクションは、ジェネリック インターフェイスを実装する必要があります |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 20538a6729b1221d4559e65eae957b0125df7e4b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: コレクションは、ジェネリック インターフェイスを実装しなければなりません
|||  
|-|-|  
|TypeName|CollectionsShouldImplementGenericInterface|  
|CheckId|CA1010|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|なし|  
  
## <a name="cause"></a>原因  
 外部から参照できる型が実装する、<xref:System.Collections.IEnumerable?displayProperty=fullName>インターフェイスしますが、実装されません、<xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>インターフェイスと、包含アセンブリの対象[!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)]です。 この規則を実装する型<xref:System.Collections.IDictionary?displayProperty=fullName>です。  
  
## <a name="rule-description"></a>規則の説明  
 コレクションの操作性を拡充するために、ジェネリック コレクション インターフェイスの 1 つを実装します。 コレクションは、次などのジェネリック コレクション型を設定を使用できます。  
  
-   <xref:System.Collections.Generic.List%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、次のジェネリック コレクション インターフェイスの 1 つを実装します。  
  
-   <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>  
  
-   <xref:System.Collections.Generic.IList%601?displayProperty=fullName>  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 この規則による警告を抑制しても安全です。ただし、コレクションより限定的に使用があります。  
  
## <a name="example-violation"></a>違反の例  
  
### <a name="description"></a>説明  
 次の例では、非ジェネリックから派生するクラス (参照型)`CollectionBase`クラスは、この規則に違反します。  
  
### <a name="code"></a>コード  
 [!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]  
  
### <a name="comments"></a>コメント  
 この規則違反を修正する必要がありますか、ジェネリック インターフェイスを実装または変更する、基本クラス既になど両方ジェネリックと非ジェネリック インターフェイスを実装する型を`Collection<T>`クラスです。  
  
## <a name="fix-by-base-class-change"></a>基本クラスの変更を修正します。  
  
### <a name="description"></a>説明  
 次の例から、非ジェネリック コレクションの基本クラスを変更することで違反を修正する`CollectionBase`ジェネリック クラス`Collection<T>`(`Collection(Of T)`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) クラス。  
  
### <a name="code"></a>コード  
 [!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]  
  
### <a name="comments"></a>コメント  
 既にリリースされてクラスの基本クラスを変更すると、既存のコンシューマーに重大な変更と見なされます。  
  
## <a name="fix-by-interface-implementation"></a>インターフェイスの実装を修正します。  
  
### <a name="description"></a>説明  
 次の例は、これらのジェネリック インターフェイスを実装することで違反を修正: `IEnumerable<T>`、 `ICollection<T>`、および`IList<T>`(`IEnumerable(Of T)`、 `ICollection(Of T)`、および`IList(Of T)`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)])。  
  
### <a name="code"></a>コード  
 [!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1005: ジェネリック型でパラメーターを使用しすぎないでください](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)  
  
 [CA1000: ジェネリック型の静的メンバーを宣言しません](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)  
  
 [CA1002: ジェネリック リストを公開しません](../code-quality/ca1002-do-not-expose-generic-lists.md)  
  
 [CA1006: ジェネリック型をメンバー シグネチャ内で入れ子にしません](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)  
  
 [CA1004: ジェネリック メソッドは型パラメーターを指定しなければなりません](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)  
  
 [CA1003: 汎用イベント ハンドラーのインスタンスを使用します](../code-quality/ca1003-use-generic-event-handler-instances.md)  
  
 [CA1007: 適切な場所にジェネリックを使用します](../code-quality/ca1007-use-generics-where-appropriate.md)  
  
## <a name="see-also"></a>参照  
 [ジェネリック](/dotnet/csharp/programming-guide/generics/index)