---
title: CA1721:プロパティ名は get メソッドと同一にすることはできません
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
helpviewer_keywords:
- CA1721
- PropertyNamesShouldNotMatchGetMethods
ms.assetid: 45a0e853-1f06-4688-af1b-cc634409e295
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d34af9e8bc814e96976fd451dc64227c730646d2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981962"
---
# <a name="ca1721-property-names-should-not-match-get-methods"></a>CA1721:プロパティ名は get メソッドと同一にすることはできません

|||
|-|-|
|TypeName|PropertyNamesShouldNotMatchGetMethods|
|CheckId|CA1721|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト メンバーの名前は、'Get' で始まるし、それ以外の場合、パブリックまたはプロテクト プロパティの名前に一致します。 たとえば、'GetColor' と '色' というプロパティがという名前のメソッドを含む型では、この規則に違反します。

## <a name="rule-description"></a>規則の説明
 Get メソッドとプロパティには、名前の関数を明確に区別する必要があります。

 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 この一貫性では、新しいソフトウェア ライブラリに必要なライブラリがマネージ コード開発の専門知識を持っている人によって開発されたという信頼を顧客になり時間が短縮します。

## <a name="how-to-fix-violations"></a>違反の修正方法
 名前を変更するは、'Get' が付いているメソッドの名前が一致しないようにします。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告は抑制しないでください。

> [!NOTE]
> IExtenderProvider インターフェイスを実装することで、Get メソッドが発生した場合は、この警告を除外することがあります。

## <a name="example"></a>例
 次の例には、メソッドとプロパティをこの規則に違反が含まれています。

 [!code-csharp[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/CSharp/ca1721-property-names-should-not-match-get-methods_1.cs)]
 [!code-vb[FxCop.Naming.GetMethod#1](../code-quality/codesnippet/VisualBasic/ca1721-property-names-should-not-match-get-methods_1.vb)]

## <a name="related-rules"></a>関連するルール
 [CA 1024:適切な場所のプロパティを使用します。](../code-quality/ca1024-use-properties-where-appropriate.md)