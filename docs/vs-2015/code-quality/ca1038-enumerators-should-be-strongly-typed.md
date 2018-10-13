---
title: '1038: 列挙子は厳密に型指定 |Microsoft Docs'
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
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 94b154fe1069c9c9af61ca955fc25da9677c5fde
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49180324"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: 列挙子は厳密に型指定されていなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト型が実装<xref:System.Collections.IEnumerator?displayProperty=fullName>の厳密に型指定されたバージョンは示しませんが、<xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName>プロパティ。 次の種類から派生した型は、この規則から除外されます。

-   <xref:System.Collections.CollectionBase?displayProperty=fullName>

-   <xref:System.Collections.DictionaryBase?displayProperty=fullName>

-   <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>規則の説明
 この規則で<xref:System.Collections.IEnumerator>を実装することも、厳密に型指定されたバージョンの<xref:System.Collections.IEnumerator.Current%2A>プロパティ ユーザーは、インターフェイスによって提供される機能を使用するときに、厳密な型を戻り値をキャストする必要がないようにします。 このルールは、実装する型前提としています。<xref:System.Collections.IEnumerator>よりも厳密な型のインスタンスのコレクションを格納<xref:System.Object>します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、インターフェイスのプロパティを明示的に実装 (として宣言`IEnumerator.Current`)。 パブリックとして宣言された、プロパティの厳密に型指定されたバージョンを追加`Current`、厳密に型指定されたオブジェクトを返します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 バイナリ ツリーなどのオブジェクト ベースのコレクションで使用するオブジェクトに基づく列挙子を実装する場合は、この規則による警告を抑制します。 新しいコレクションを拡張する型では、厳密に型指定の列挙子を定義し、厳密に型指定されたプロパティを公開します。

## <a name="example"></a>例
 次の例では、厳密に型指定を実装する正しい方法<xref:System.Collections.IEnumerator>型。

 [!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.IEnumeratorStrongTypes/cs/FxCop.Design.IEnumeratorStrongTypes.cs#1)]

## <a name="related-rules"></a>関連規則
 [CA1035: ICollection の実装は、厳密に型指定されたメンバーを含んでいます](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

 [CA1039: リストは厳密に型指定されています](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>関連項目
 <xref:System.Collections.IEnumerator?displayProperty=fullName> <xref:System.Collections.CollectionBase?displayProperty=fullName>
 <xref:System.Collections.DictionaryBase?displayProperty=fullName>
 <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>



