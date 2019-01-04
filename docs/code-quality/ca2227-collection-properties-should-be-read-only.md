---
title: CA2227:Collection プロパティは読み取り専用でなければなりません
ms.date: 09/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
- CPP
ms.workload:
- multiple
ms.openlocfilehash: 085bf631a444dc3b6dc64dba4ef10d111f6492bb
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949064"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227:Collection プロパティは読み取り専用でなければなりません

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

実装する型の外部から参照できる、書き込み可能なプロパティは、<xref:System.Collections.ICollection?displayProperty=fullName>します。 このルールは、配列、インデクサー ('Item' という名前のプロパティ)、およびアクセス許可セットは無視されます。

## <a name="rule-description"></a>規則の説明

書き込み可能なコレクション プロパティには、完全に別のコレクションで置換するユーザーができます。 読み取り専用プロパティは、置き換えられるからコレクションを停止しますが、引き続き、個々 のメンバーを設定することができます。 コレクションの置換が目標の場合、推奨される設計パターンが、コレクションからすべての要素を削除するメソッドをおよびコレクションを再作成するためのメソッドが含まれます。 参照してください、<xref:System.Collections.ArrayList.Clear%2A>と<xref:System.Collections.ArrayList.AddRange%2A>のメソッド、<xref:System.Collections.ArrayList?displayProperty=fullName>このパターンの例のクラス。

バイナリおよび XML シリアル化の両方は、コレクションである読み取り専用のプロパティをサポートします。 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>クラスに実装する型の特定の要件は<xref:System.Collections.ICollection>と<xref:System.Collections.IEnumerable?displayProperty=fullName>シリアル化可能にするためにします。

## <a name="how-to-fix-violations"></a>違反の修正方法

このルールの違反を修正するには、読み取り専用プロパティを作成します。 設計上必要な場合は、オフにし、コレクションを再作成するメソッドを追加します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

プロパティの一部である場合、警告を抑制することができます、[データ転送オブジェクト (DTO)](/previous-versions/msp-n-p/ff649585(v=pandp.10))クラス。

それ以外の場合、この規則による警告を抑制しないでください。

## <a name="example"></a>例

次の例では、書き込み可能なコレクションのプロパティを持つ型を表示し、コレクションを直接置換する方法を示しています。 また、適切なを使用して読み取り専用のコレクション プロパティを置き換える方法を説明`Clear`と`AddRange`メソッド。

[!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
[!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
[!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>関連するルール

- [CA 1819:プロパティは、配列を返す必要がありますいません。](../code-quality/ca1819-properties-should-not-return-arrays.md)