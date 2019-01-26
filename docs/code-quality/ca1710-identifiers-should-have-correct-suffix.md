---
title: CA1710:識別子は、正しいサフィックスを含んでいなければなりません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fa39e361d7659e4508c916fc7681ac3b0c5fdd1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55029857"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710:識別子は、正しいサフィックスを含んでいなければなりません

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

識別子には、正しいサフィックスはありません。

## <a name="rule-description"></a>規則の説明

慣例により、特定の基本型を拡張するか、特定のインターフェイス、またはこれらの型から派生した型を実装する型の名前には、基本データ型またはインターフェイスに関連付けられているサフィックスを持ちます。

名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージド コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。

次の表は、基本型とサフィックスが関連付けられているインターフェイスを示します。

|基本型/インターフェイス|サフィックス|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|属性|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|例外|
|<xref:System.Collections.ICollection?displayProperty=fullName>|コレクション|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Dictionary|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|コレクション|
|<xref:System.Collections.Queue?displayProperty=fullName>|コレクションまたはキュー|
|<xref:System.Collections.Stack?displayProperty=fullName>|コレクションまたはスタック|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|コレクション|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Dictionary|
|<xref:System.Data.DataSet?displayProperty=fullName>|データセット|
|<xref:System.Data.DataTable?displayProperty=fullName>|コレクションまたは DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|ストリーム|
|<xref:System.Security.IPermission?displayProperty=fullName>|アクセス許可|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|条件|
|イベント ハンドラーのデリゲート。|EventHandler|

実装する型<xref:System.Collections.ICollection>ディクショナリ、スタック、またはキューが使用できる型の使用目的について意味のある情報を提供する名などがあります、データ構造の一般的な型とします。

実装する型<xref:System.Collections.ICollection>は特定の項目のコレクションが 'Collection' で終わる名前があるとします。 たとえばのコレクション<xref:System.Collections.Queue>オブジェクト名 'QueueCollection' になります。 'Collection' サフィックスを使用して、コレクションのメンバーを列挙できることを示します、 `foreach` (`For Each`で[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) ステートメント。

実装する型<xref:System.Collections.IDictionary>型も実装している場合でも、「ディクショナリ」で終わる名前を持つ<xref:System.Collections.IEnumerable>または<xref:System.Collections.ICollection>します。 'Collection' および 'ディクショナリ' サフィックス名前付け規則は、次の 2 つの列挙型パターンを区別するユーザーを有効にします。

'Collection' サフィックスを持つ型では、この列挙型パターンに従います。

```
foreach(SomeType x in SomeCollection) { }
```

'ディクショナリ' サフィックスを持つ型では、この列挙型パターンに従います。

```
foreach(SomeType x in SomeDictionary.Values) { }
```

A<xref:System.Data.DataSet>オブジェクトのコレクションから成る<xref:System.Data.DataTable>、オブジェクトのコレクションで構成される<xref:System.Data.DataColumn?displayProperty=fullName>と<xref:System.Data.DataRow?displayProperty=fullName>他のユーザーの間でのオブジェクト。 これらのコレクションを実装<xref:System.Collections.ICollection>ベースを通じて<xref:System.Data.InternalDataCollectionBase?displayProperty=fullName>クラス。

## <a name="how-to-fix-violations"></a>違反の修正方法

型の名前を変更して、正しい用語が付くようにします。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

型が拡張される可能性がある場合や、さまざまな項目の任意のセットを保持する、汎用的なデータ構造の場合は、'Collection' サフィックスを使用する警告を抑制しても安全です。 ここでは、名前、実装、パフォーマンス、またはデータ構造体の他の特性に関する有益情報を提供する必要があります (たとえば、BinaryTree)。 型が、特定の種類 (たとえば、StringCollection) のコレクションを表す場合、サフィックスを使用して、型を列挙できることを示しているためこの規則による警告を抑制しないで、`foreach`ステートメント。

他のサフィックスの場合は、この規則による警告を抑制しないでください。 サフィックスは、型名から明らかにする目的の使用を許可します。

## <a name="related-rules"></a>関連するルール

[CA1711:識別子には、不適切なサフィックスはありません。](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>関連項目

- [属性](/dotnet/standard/design-guidelines/attributes)
- [処理とイベントの発生](/dotnet/standard/events/index)