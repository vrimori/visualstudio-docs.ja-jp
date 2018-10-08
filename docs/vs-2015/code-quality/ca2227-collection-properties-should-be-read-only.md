---
title: '2227: コレクションのプロパティは読み取りなりませんのみ |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
helpviewer_keywords:
- CA2227
- CollectionPropertiesShouldBeReadOnly
ms.assetid: 26967aaf-6fbe-438a-b4d3-ac579b5dc0f9
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c9c91a0e563c7e83157dcff06e982c1bda40c5b5
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589178"
---
# <a name="ca2227-collection-properties-should-be-read-only"></a>CA2227: Collection プロパティは読み取り専用でなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA2227: コレクションのプロパティは読み取り専用にする](https://docs.microsoft.com/visualstudio/code-quality/ca2227-collection-properties-should-be-read-only)します。

|||
|-|-|
|TypeName|CollectionPropertiesShouldBeReadOnly|
|CheckId|CA2227|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 外部から見えるの書き込み可能なプロパティが実装する型<xref:System.Collections.ICollection?displayProperty=fullName>します。 ルールでは、配列、インデクサー ('Item' という名前のプロパティ)、およびアクセス許可セットは無視されます。

## <a name="rule-description"></a>規則の説明
 書き込み可能なコレクション プロパティには、完全に別のコレクションで置換するユーザーができます。 読み取り専用プロパティは、コレクションを置換できないようにしますが、個別のメンバーが設定されることは回避できません。 コレクションの置換が目標の場合、推奨される設計パターンが、コレクションからすべての要素を削除するメソッドをおよびコレクションを再設定するメソッドが含まれます。 参照してください、<xref:System.Collections.ArrayList.Clear%2A>と<xref:System.Collections.ArrayList.AddRange%2A>のメソッド、<xref:System.Collections.ArrayList?displayProperty=fullName>このパターンの例のクラス。

 バイナリおよび XML シリアル化の両方は、コレクションである読み取り専用のプロパティをサポートします。 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>クラスに実装する型の特定の要件は<xref:System.Collections.ICollection>と<xref:System.Collections.IEnumerable?displayProperty=fullName>シリアル化可能にするためにします。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、読み取り専用プロパティを作成し、設計上必要な場合をオフにし、コレクションを再作成するメソッドを追加します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、書き込み可能なコレクションのプロパティを持つ型を表示し、コレクションを直接置換する方法を示しています。 推奨される方法を使用して読み取り専用のコレクション プロパティに置き換えるさらに、`Clear`と`AddRange`メソッドが表示されます。

 [!code-cpp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cpp/FxCop.Usage.PropertiesReturningCollections.cpp#1)]
 [!code-csharp[FxCop.Usage.PropertiesReturningCollections#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/cs/FxCop.Usage.PropertiesReturningCollections.cs#1)]
 [!code-vb[FxCop.Usage.PropertiesReturningCollections#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.PropertiesReturningCollections/vb/FxCop.Usage.PropertiesReturningCollections.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1819: プロパティは、配列を返すことはできません](../code-quality/ca1819-properties-should-not-return-arrays.md)



