---
title: "CA1038: 列挙子は厳密に型指定 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 84ddea0bebd5c3811da84abadd207b839ec8be48
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: 列挙子は厳密に型指定されていなければなりません
|||  
|-|-|  
|TypeName|EnumeratorsShouldBeStronglyTyped|  
|CheckId|CA1038|  
|カテゴリ|Microsoft.Design|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 パブリックまたはプロテクト型が実装する<xref:System.Collections.IEnumerator?displayProperty=fullName>の厳密に型指定されたバージョンは提供されません、<xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName>プロパティです。 次の種類から派生した型は、この規則から除外されます。  
  
-   <xref:System.Collections.CollectionBase?displayProperty=fullName>  
  
-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>  
  
-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>  
  
## <a name="rule-description"></a>規則の説明  
 この規則で<xref:System.Collections.IEnumerator>厳密に型指定されたバージョンの指定を実装する、<xref:System.Collections.IEnumerator.Current%2A>プロパティ ユーザーは、インターフェイスによって提供される機能を使用するときに、厳密な型への戻り値をキャストする必要がないようにします。 このルールは、ある型を実装する前提としています。<xref:System.Collections.IEnumerator>よりも厳密な型のインスタンスのコレクションを含んでいます<xref:System.Object>です。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 この規則違反を修正するには、インターフェイスのプロパティを明示的に実装 (として宣言`IEnumerator.Current`)。 パブリックの厳密に型指定されたバージョンとして宣言されている、プロパティの追加`Current`、厳密に型指定されたオブジェクトを返すことがあるとします。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 バイナリ ツリーなどのオブジェクト ベースのコレクションで使用するオブジェクトに基づく列挙子を実装する場合は、この規則による警告を抑制します。 新しいコレクションを拡張する型は厳密に型指定の列挙子を定義し、厳密に型指定のプロパティを公開します。  
  
## <a name="example"></a>例  
 次の例では、厳密に型を実装するための正しい方法<xref:System.Collections.IEnumerator>型です。  
  
 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]  
  
## <a name="related-rules"></a>関連規則  
 [CA1035: ICollection の実装は、厳密に型指定されたメンバーを含んでいます](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)  
  
 [CA1039: リストは厳密に型指定されています](../code-quality/ca1039-lists-are-strongly-typed.md)  
  
## <a name="see-also"></a>参照  
 <xref:System.Collections.IEnumerator?displayProperty=fullName>   
 <xref:System.Collections.CollectionBase?displayProperty=fullName>   
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>   
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>