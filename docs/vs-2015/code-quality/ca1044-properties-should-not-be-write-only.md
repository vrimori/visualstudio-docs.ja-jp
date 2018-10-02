---
title: 'Ca 1044: プロパティが書き込み専用することはできません |Microsoft Docs'
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
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 732af1dcdeff669723f717dabe035a38640a8bf3
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47592374"
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: プロパティを書き込み専用にすることはできません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 1044: プロパティは書き込み専用できません](https://docs.microsoft.com/visualstudio/code-quality/ca1044-properties-should-not-be-write-only)します。

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

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告を抑制しないでくださいを強くお勧めします。

## <a name="example"></a>例
 次の例では、`BadClassWithWriteOnlyProperty`は書き込み専用プロパティを持つ型。 `GoodClassWithReadWriteProperty` 修正後のコードが含まれています。

 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/cs/FxCop.Design.PropertiesNotWriteOnly.cs#1)]
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.PropertiesNotWriteOnly/vb/PropertiesNotWriteOnly.vb#1)]



