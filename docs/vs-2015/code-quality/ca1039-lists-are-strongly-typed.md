---
title: '1039: ca リストは厳密に型指定 |Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 681c1ada7600743c0a548f8a774dada6863f7d0d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853416"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: リストは厳密に型指定されています
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ListsAreStronglyTyped|
|CheckId|CA1039|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型実装<xref:System.Collections.IList?displayProperty=fullName>は、次の 1 つ以上の厳密に型指定されたメソッドを提供しません。

-   IList.Item

-   IList.Add

-   IList.Contains

-   IList.IndexOf

-   IList.Insert

-   IList.Remove

## <a name="rule-description"></a>規則の説明
 この規則で<xref:System.Collections.IList>を実装する厳密に型指定されたメンバー ユーザーは引数をキャストする必要がないように、<xref:System.Object?displayProperty=fullName>インターフェイスによって提供される機能を使用するときに入力します。 <xref:System.Collections.IList>インターフェイス インデックスによってアクセスできるオブジェクトのコレクションによって実装されます。 このルールは、実装する型前提としています。<xref:System.Collections.IList>はこれよりも厳密な型のインスタンスのコレクションを管理する<xref:System.Object>します。

 <xref:System.Collections.IList> 実装して、<xref:System.Collections.ICollection?displayProperty=fullName>と<xref:System.Collections.IEnumerable?displayProperty=fullName>インターフェイス。 実装する場合<xref:System.Collections.IList>の必須の厳密に型指定されたメンバーを提供する必要があります<xref:System.Collections.ICollection>します。 コレクション内のオブジェクトを拡張する場合<xref:System.ValueType?displayProperty=fullName>の厳密に型指定されたメンバーを提供する必要があります<xref:System.Collections.IEnumerable.GetEnumerator%2A>パフォーマンスの低下を回避するためにボックス化によって発生した、コレクションの参照型である場合は必要ありません。

 このルールに準拠するインターフェイス メンバーを明示的に実装など、InterfaceName.InterfaceMemberName 形式で名前を使用して<xref:System.Collections.IList.Add%2A>します。 明示的なインターフェイス メンバーは、インターフェイスで宣言されているデータ型を使用します。 インターフェイス メンバーの名前を使用して、厳密に型指定されたメンバーを実装`Add`します。 Public として厳密に型指定されたメンバーを宣言して、パラメーターを宣言およびコレクションで管理されている厳密な型の値を返します。 厳密な型より強度の低い種類を置き換える<xref:System.Object>と<xref:System.Array>インターフェイスで宣言されています。

## <a name="how-to-fix-violations"></a>違反の修正方法
 このルールの違反を修正するには、明示的に実装<xref:System.Collections.IList>メンバーと、前にメモしたメンバーの厳密に型指定の代替手段を提供します。 正しく実装したコードについて、<xref:System.Collections.IList>インターフェイスし、提供に必要な厳密に型指定されたメンバーは、次の例を参照してください。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 新しいコレクションを拡張する型が厳密な型を判断、リンク リストなどの新しいオブジェクトに基づくコレクションを実装する場合は、この規則による警告を抑制します。 これらの型は、この規則に準拠し、厳密に型指定されたメンバーを公開する必要があります。

## <a name="example"></a>例
 次の例では、型`YourType`拡張<xref:System.Collections.CollectionBase?displayProperty=fullName>、厳密に型指定されたすべてのコレクションをする必要があります。 なお<xref:System.Collections.CollectionBase>の明示的な実装を提供します、<xref:System.Collections.IList>のためのインターフェイス。 そのため、する必要がありますのみを指定の厳密に型指定されたメンバー<xref:System.Collections.IList>と<xref:System.Collections.ICollection>します。

 [!code-csharp[FxCop.Design.IListStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IListStrongTypes/cs/FxCop.Design.IListStrongTypes.cs#1)]

## <a name="related-rules"></a>関連規則
 [CA1035: ICollection の実装は、厳密に型指定されたメンバーを含んでいます](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1038: 列挙子は厳密に型指定されていなければなりません](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>関連項目
 <xref:System.Collections.CollectionBase?displayProperty=fullName> <xref:System.Collections.ICollection?displayProperty=fullName>
 <xref:System.Collections.IEnumerable?displayProperty=fullName>
 <xref:System.Collections.IList?displayProperty=fullName>
 <xref:System.Object?displayProperty=fullName>



