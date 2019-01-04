---
title: CA1035:ICollection の実装は、厳密に型指定されたメンバーを含んでいます
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9a1695ee55c8142a170fae41a1143118e0ba5a53
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949077"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035:ICollection の実装は、厳密に型指定されたメンバーを含んでいます

|||
|-|-|
|TypeName|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型が実装<xref:System.Collections.ICollection?displayProperty=fullName>の厳密に型指定されたメソッドは提供されません<xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>します。 厳密に型指定されたバージョンの<xref:System.Collections.ICollection.CopyTo%2A>2 つのパラメーターを受け入れる必要があり、含めることはできません、<xref:System.Array?displayProperty=fullName>または配列の<xref:System.Object?displayProperty=fullName>最初のパラメーターとして。

## <a name="rule-description"></a>規則の説明
 この規則で<xref:System.Collections.ICollection>を実装する厳密に型指定されたメンバー ユーザーは引数をキャストする必要がないように、<xref:System.Object>インターフェイスによって提供される機能を使用するときに入力します。 このルールは、実装する型前提としています。<xref:System.Collections.ICollection>がよりも厳密な型のインスタンスのコレクションを管理するため<xref:System.Object>します。

 <xref:System.Collections.ICollection> は、<xref:System.Collections.IEnumerable?displayProperty=fullName> インターフェイスを実装します。 場合は、コレクション内のオブジェクトの拡張<xref:System.ValueType?displayProperty=fullName>の厳密に型指定されたメンバーを提供する必要があります<xref:System.Collections.IEnumerable.GetEnumerator%2A>ボックス化によって発生したパフォーマンスの低下を回避するためにします。 これは、コレクションの参照型である場合に必要ありません。

 インターフェイス メンバーの厳密に型指定されたバージョンを実装するインターフェイス メンバーを明示的に実装形式で名前を使用して、`InterfaceName.InterfaceMemberName`など<xref:System.Collections.ICollection.CopyTo%2A>します。 明示的なインターフェイス メンバーは、インターフェイスで宣言されているデータ型を使用します。 インターフェイス メンバーの名前を使用して、厳密に型指定されたメンバーを実装<xref:System.Collections.ICollection.CopyTo%2A>します。 Public として厳密に型指定されたメンバーを宣言して、パラメーターを宣言およびコレクションで管理されている厳密な型の値を返します。 厳密な型より強度の低い種類を置き換える<xref:System.Object>と<xref:System.Array>インターフェイスで宣言されています。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、インターフェイス メンバーを明示的に実装 (として宣言<xref:System.Collections.ICollection.CopyTo%2A>)。 として宣言されている、パブリックの厳密に型指定されたメンバーを追加`CopyTo`、最初のパラメーターとして厳密に型指定された配列を取得することです。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 バイナリ ツリーは、新しいコレクションを拡張する型が厳密な型を決定などの新しいオブジェクトに基づくコレクションを実装する場合は、この規則による警告を抑制します。 これらの型は、この規則に準拠し、厳密に型指定されたメンバーを公開する必要があります。

## <a name="example"></a>例
 次の例では、実装する正しい方法<xref:System.Collections.ICollection>します。

 [!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]

## <a name="related-rules"></a>関連するルール
 [CA1038:列挙子を厳密に型指定する必要があります。](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

 [CA1039:リストは厳密に型指定します。](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>関連項目

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>