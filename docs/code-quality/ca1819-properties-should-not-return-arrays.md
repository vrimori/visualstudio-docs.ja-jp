---
title: 'CA1819: プロパティは、配列を返すことはできません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 68f64d37a7616f095a86452353edc498d2d27f28
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45549418"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: プロパティは、配列を返すことはできません

|||
|-|-|
|TypeName|PropertiesShouldNotReturnArrays|
|CheckId|CA1819|
|カテゴリ|Microsoft.Performance|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリック型の public または protected のプロパティでは、配列を返します。

## <a name="rule-description"></a>規則の説明
 プロパティによって返される配列は、プロパティが読み取り専用の場合でも書き込み保護されていません。 配列の改ざんを防ぐには、プロパティで配列のコピーを返す必要があります。 一般に、このようなプロパティを呼び出すときのパフォーマンス低下は理解されません。 具体的には、インデックス付きプロパティとしてプロパティを使用する可能性があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、メソッド、プロパティを作成するかコレクションを取得するプロパティを変更します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 属性は、配列を返すプロパティを含めることができますが、コレクションを返すプロパティを含めることはできません。 派生した属性のプロパティに対して発生する警告を抑制することができます、<xref:System.Attribute>クラス。 それ以外の場合、この規則による警告を抑制しないでください。

## <a name="example-violation"></a>例の違反

### <a name="description"></a>説明
 次の例では、この規則に違反するプロパティを示します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_1.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_1.vb)]

### <a name="comments"></a>コメント
 この規則違反を修正するには、メソッド、プロパティを作成するか配列の代わりにコレクションを取得するプロパティを変更します。

## <a name="change-the-property-to-a-method-example"></a>プロパティ メソッドの例に変更します。

### <a name="description"></a>説明
 次の例では、メソッド、プロパティを変更することで、違反を修正します。

### <a name="code"></a>コード
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_2.vb)]
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_2.cs)]

## <a name="return-a-collection-example"></a>コレクションを返す例

### <a name="description"></a>説明
 次の例が返されるプロパティを変更することで、違反を修正します。

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_3.cs)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_3.vb)]

## <a name="allowing-users-to-modify-a-property"></a>プロパティを変更するユーザーを許可します。

### <a name="description"></a>説明
 プロパティを変更するクラスのコンシューマーを許可する場合があります。 次の例では、この規則に違反する読み取り/書き込みプロパティを示します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_4.cs)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_4.vb)]

### <a name="comments"></a>コメント
 次の例では、返されるプロパティを変更することで、違反を修正する、<xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>します。

### <a name="code"></a>コード
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/VisualBasic/ca1819-properties-should-not-return-arrays_5.vb)]
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../code-quality/codesnippet/CSharp/ca1819-properties-should-not-return-arrays_5.cs)]

## <a name="related-rules"></a>関連するルール
 [CA1024: 適切な場所にプロパティを使用します](../code-quality/ca1024-use-properties-where-appropriate.md)