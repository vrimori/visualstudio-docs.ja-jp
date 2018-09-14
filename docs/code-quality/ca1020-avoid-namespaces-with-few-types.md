---
title: 'CA1020: 型をほとんど含まない名前空間を使用しません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
helpviewer_keywords:
- CA1020
- AvoidNamespacesWithFewTypes
ms.assetid: 9cb272f6-a3ff-45af-b35d-70dea620b074
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fc7a691cb5c5626ea096046e277ec3d1655db0b6
ms.sourcegitcommit: 568bb0b944d16cfe1af624879fa3d3594d020187
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2018
ms.locfileid: "45546221"
---
# <a name="ca1020-avoid-namespaces-with-few-types"></a>CA1020: 型をほとんど含まない名前空間を使用しません

|||
|-|-|
|TypeName|AvoidNamespacesWithFewTypes|
|CheckId|CA1020|
|カテゴリ|Microsoft.Design|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因

グローバル名前空間以外の名前空間には、5 未満の型が含まれています。

## <a name="rule-description"></a>規則の説明

各名前空間には、論理的な少ない名前空間で型を配置する正当な理由が存在することを確認します。 名前空間には、ほとんどのシナリオで同時に使用される型を含める必要があります。 自分のアプリケーションが相互に排他的な場合は、個別の名前空間で型を配置する必要があります。 たとえば、<xref:System.Web.UI>名前空間には、web アプリケーションで使用される型が含まれています。 および<xref:System.Windows.Forms>名前空間で使用される型が含まれています[!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]-ベースのアプリケーション。 両方の名前空間では、ユーザー インターフェイスの側面を制御する型がある、でも、これらの型では、同じアプリケーションで使用する設計されていません。 そのため、個別の名前空間内にあります。 注意名前空間の組織も役に立ちます機能の探索可能性が増えるためです。 名前空間の階層を確認するには、ライブラリのコンシューマーは、機能を実装する型を特定できる必要があります。

> [!NOTE]
> このガイドラインに準拠する他の名前空間には、デザイン時の型とアクセス許可しないマージする必要があります。 メインの名前空間の下に独自の名前空間に属しているこれらの型と名前空間の末尾に`.Design`と`.Permissions`、それぞれします。

## <a name="how-to-fix-violations"></a>違反の修正方法

この規則違反を修正するのには、単一の名前空間にはいくつかの種類を含む名前空間を結合するしてみてください。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。

名前空間には、他の名前空間の型で使用される型が含まれていない場合、このルールから警告を抑制しても安全です。