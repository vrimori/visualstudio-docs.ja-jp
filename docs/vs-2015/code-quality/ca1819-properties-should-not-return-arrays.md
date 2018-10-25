---
title: 'Ca 1819: プロパティは配列を返すありません |Microsoft Docs'
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
- PropertiesShouldNotReturnArrays
- CA1819
helpviewer_keywords:
- PropertiesShouldNotReturnArrays
- CA1819
ms.assetid: 85fcf312-57f8-438a-8b10-34441fe0bdeb
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6591431edf7ca6de84bbf18d431ad7350308a172
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881730"
---
# <a name="ca1819-properties-should-not-return-arrays"></a>CA1819: プロパティは、配列を返すことはできません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 属性は、配列を返すプロパティを含めることができますが、コレクションを返すプロパティを含めることはできません。 [System.Attribute] から派生した属性のプロパティに対して発生する警告を抑制することができます (<!-- TODO: review code entity reference <xref:assetId:///System.Attribute?qualifyHint=False&amp;autoUpgrade=True>  -->) クラス。 それ以外の場合、この規則による警告を抑制しないでください。

## <a name="example-violation"></a>例の違反

### <a name="description"></a>説明
 次の例では、この規則に違反するプロパティを示します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Performance.PropertyArrayViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/cs/FxCop.Performance.PropertyArrayViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayViolation/vb/FxCop.Performance.PropertyArrayViolation.vb#1)]

### <a name="comments"></a>コメント
 この規則違反を修正するには、メソッド、プロパティを作成するか配列の代わりにコレクションを取得するプロパティを変更します。

## <a name="change-the-property-to-a-method-example"></a>プロパティ メソッドの例に変更します。

### <a name="description"></a>説明
 次の例では、メソッド、プロパティを変更することで、違反を修正します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/cs/FxCop.Performance.PropertyArrayFixedMethod.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedMethod#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedMethod/vb/FxCop.Performance.PropertyArrayFixedMethod.vb#1)]

## <a name="return-a-collection-example"></a>コレクションを返す例

### <a name="description"></a>説明
 次の例が返されるプロパティを変更することで、違反を修正します。

 <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/cs/FxCop.Performance.PropertyArrayFixedCollection.cs#1)]
 [!code-vb[FxCop.Performance.PropertyArrayFixedCollection#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyArrayFixedCollection/vb/FxCop.Performance.PropertyArrayFixedCollection.vb#1)]

## <a name="allowing-users-to-modify-a-property"></a>プロパティを変更するユーザーを許可します。

### <a name="description"></a>説明
 プロパティを変更するクラスのコンシューマーを許可する場合があります。 次の例では、この規則に違反する読み取り/書き込みプロパティを示します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Performance.PropertyModifyViolation#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/cs/FxCop.Performance.PropertyModifyViolation.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyViolation#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyViolation/vb/FxCop.Performance.PropertyModifyViolation.vb#1)]

### <a name="comments"></a>コメント
 次の例では、返されるプロパティを変更することで、違反を修正する、<xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Performance.PropertyModifyFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/cs/FxCop.Performance.PropertyModifyFixed.cs#1)]
 [!code-vb[FxCop.Performance.PropertyModifyFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.PropertyModifyFixed/vb/FxCop.Performance.PropertyModifyFixed.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1024: 適切な場所にプロパティを使用します](../code-quality/ca1024-use-properties-where-appropriate.md)



