---
title: 'CA1044: プロパティを書き込み専用にすることはできません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6018957bc6de32668cbaf0a719f2a603dc7f496f
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45550987"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: プロパティを書き込み専用にすることはできません

|||
|-|-|
|TypeName|PropertiesShouldNotBeWriteOnly|
|CheckId|CA1044|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクト プロパティは、set アクセサーがありますに get アクセサーがないです。

## <a name="rule-description"></a>規則の説明
 取得アクセサー プロパティへの読み取りアクセスを提供し、set アクセサーが書き込みアクセス権を提供します。 読み取り専用のプロパティは許容され、必要な場合もよくありますが、書き込み専用のプロパティを使用することはデザインのガイドラインで禁止されています。 これは、値を設定するためから値を表示し、ユーザーが原因では、セキュリティは提供されません。 また、読み取りアクセスがないと、共有オブジェクトのステータスを参照できないため、実用性が制限されます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、プロパティに get アクセサーを追加します。 または、書き込み専用プロパティの動作が必要な場合は、このプロパティをメソッドに変換することを検討します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 この規則による警告を抑制しないことをお勧めします。

## <a name="example"></a>例
 次の例では、`BadClassWithWriteOnlyProperty`は書き込み専用プロパティを持つ型。 `GoodClassWithReadWriteProperty` 修正後のコードが含まれています。

 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]