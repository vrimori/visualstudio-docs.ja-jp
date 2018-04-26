---
title: 'CA2227: Collection プロパティは読み取り専用でなければなりません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
ms.workload:
- multiple
ms.openlocfilehash: 5a3fd69bccdfdc1c08bbc62f6534b40b746d6d49
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Collection プロパティは読み取り専用でなければなりません
|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から参照できる書き込み可能なプロパティを実装する型は、<xref:System.Collections.ICollection?displayProperty=fullName>です。 ルールでは、配列、インデクサー (名前のプロパティを 'Item')、およびアクセス許可セットが無視されます。

## <a name="rule-description"></a>規則の説明
 書き込み可能なコレクション プロパティにより、ユーザーが完全に別のコレクションで置換します。 読み取り専用プロパティは、コレクションを置換できないようにしますが、個別のメンバーが設定されることは回避できません。 コレクションを置き換えることが目標の場合、推奨されるデザイン パターンをコレクションからすべての要素を削除するメソッドなどのコレクションを再構築するメソッドを開始します。 参照してください、<xref:System.Collections.ArrayList.Clear%2A>と<xref:System.Collections.ArrayList.AddRange%2A>のメソッド、<xref:System.Collections.ArrayList?displayProperty=fullName>このパターンの例のクラスです。

 バイナリおよび XML シリアル化の両方は、読み取り専用のプロパティは、コレクションをサポートします。 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>クラスを実装する型の特定の要件には<xref:System.Collections.ICollection>と<xref:System.Collections.IEnumerable?displayProperty=fullName>シリアル化するためにします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、読み取り専用プロパティを作成し、デザイン、必要な場合をオフにして、コレクションを再作成する方法を追加します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、書き込み可能なコレクション プロパティを使用して型を示していて、コレクションを直接交換する方法を示しています。 読み取り専用コレクション プロパティを使用して、置き換える優先の方法ではさらに、`Clear`と`AddRange`方法を表示します。

 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CSharp/ca2227-collection-properties-should-be-read-only_1.cs)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/VisualBasic/ca2227-collection-properties-should-be-read-only_1.vb)]
 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../code-quality/codesnippet/CPP/ca2227-collection-properties-should-be-read-only_1.cpp)]

## <a name="related-rules"></a>関連規則
 [CA1819: プロパティは、配列を返すことはできません](../code-quality/ca1819-properties-should-not-return-arrays.md)