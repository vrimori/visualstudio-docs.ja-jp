---
title: 'Ca 1028: 列挙ストレージは Int32 でなければなりません。Microsoft Docs'
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
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 305bd87a72de1e3ad22b8cf689f10ad49939a34b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49304500"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: 列挙ストレージは Int32 でなければなりません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリック列挙体の基になる型でない<xref:System.Int32?displayProperty=fullName>します。

## <a name="rule-description"></a>規則の説明
 列挙型は、関連する名前付き定数が複数定義された値型です。 既定で、<xref:System.Int32?displayProperty=fullName>定数の値を格納するデータ型を使用します。 できます、この変更の種類を基になる場合でもないために必要なまたは推奨されるほとんどのシナリオ。 小さいデータ型を使用して大幅なパフォーマンスの向上が実現しないことに注意してください。<xref:System.Int32>します。 既定のデータ型を使用できない場合、共通言語システム (CLS) のいずれかを使用する必要があります-準拠の整数型<xref:System.Byte>、 <xref:System.Int16>、 <xref:System.Int32>、または<xref:System.Int64>列挙体のすべての値で表現できることを確認するにはCLS 準拠のプログラミング言語です。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則の違反を修正するには、サイズや互換性の問題が存在しない限り、使用<xref:System.Int32>します。 場合、<xref:System.Int32>値を保持するのに十分な大きさでない<xref:System.Int64>します。 旧バージョンとの互換性は、小さいデータ型を必要とする場合は、使用<xref:System.Byte>または<xref:System.Int16>します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 旧バージョンと互換性の問題で必要な場合にのみ、この規則による警告を抑制します。 アプリケーションでは、通常、この規則に準拠するエラーには、問題は発生しません。 ライブラリ、言語の相互運用性が必要な場合、この規則に準拠しないは、ユーザーの悪影響を及ぼす影響可能性があります。

## <a name="example-of-a-violation"></a>違反の例

### <a name="description"></a>説明
 次の例では、推奨される基になるデータ型を使用して 2 つの列挙体を示します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/cs/FxCop.Design.EnumIntegralType.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralType#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/vb/FxCop.Design.EnumIntegralType.vb#1)]

## <a name="example-of-how-to-fix"></a>修正する方法の例

### <a name="description"></a>説明
 次の例を基になるデータ型を変更することで以前の違反を修正する<xref:System.Int32>します。

### <a name="code"></a>コード
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/cs/FxCop.Design.EnumIntegralTypeFixed.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/vb/FxCop.Design.EnumIntegralTypeFixed.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1008: Enums は 0 値を含んでいなければなりません](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: FlagsAttribute で列挙値をマークします](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: enums を FlagsAttribute に設定しません](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: enum 値に 'Reserved' という名前を指定しません](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: enum 値を型名のプレフィックスにしません](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>関連項目
 <xref:System.Byte?displayProperty=fullName> <xref:System.Int16?displayProperty=fullName>
 <xref:System.Int32?displayProperty=fullName>
 <xref:System.Int64?displayProperty=fullName>



