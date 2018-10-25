---
title: 'Ca 1712: enum 値を型名のプレフィックスにしません |Microsoft Docs'
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
- CA1712
- DoNotPrefixEnumValuesWithTypeName
helpviewer_keywords:
- CA1712
- DoNotPrefixEnumValuesWithTypeName
ms.assetid: df0e3a12-67bf-48f1-a10b-2ef60484a5c7
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: eba81742eefd4e5a89e98417c8530f3146133916
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49916726"
---
# <a name="ca1712-do-not-prefix-enum-values-with-type-name"></a>CA1712: enum 値を型名のプレフィックスにしません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotPrefixEnumValuesWithTypeName|
|CheckId|CA1712|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 列挙には、列挙体の型名で始まる名前を持つメンバーが含まれています。

## <a name="rule-description"></a>規則の説明
 列挙型メンバーの名前は、開発ツールが提供する型情報が予想されるため、型名でが付きますされません。

 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これには、新しいソフトウェア ライブラリを習得するために必要であり、ライブラリがマネージ コード開発の専門知識を持っている人によって開発されたという信頼を顧客が増加する時間が短縮されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、列挙型のメンバーから、型名のプレフィックスを削除します。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。

## <a name="example"></a>例
 次の例では、列挙型が不適切な名前であることを後に修正されたバージョンを示します。

 [!code-cpp[FxCop.Naming.EnumValues#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/cpp/FxCop.Naming.EnumValues.cpp#1)]
 [!code-csharp[FxCop.Naming.EnumValues#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/cs/FxCop.Naming.EnumValues.cs#1)]
 [!code-vb[FxCop.Naming.EnumValues#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Naming.EnumValues/vb/FxCop.Naming.EnumValues.vb#1)]

## <a name="related-rules"></a>関連規則
 [CA1711: 識別子は、不適切なサフィックスを含むことはできません](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

 [CA1027: FlagsAttribute で列挙値をマークします](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: enums を FlagsAttribute に設定しません](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>関連項目
 <xref:System.Enum?displayProperty=fullName>



