---
title: 'Ca 2211: 非定数フィールドは表示されません |Microsoft Docs'
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
- CA2211
- NonConstantFieldsShouldNotBeVisible
helpviewer_keywords:
- NonConstantFieldsShouldNotBeVisible
- CA2211
ms.assetid: e1e42c40-0acd-4312-af29-70133739a304
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 62c3ee28a3b7cbb9bef864483e254dda5f63bfae
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49894255"
---
# <a name="ca2211-non-constant-fields-should-not-be-visible"></a>CA2211: 非定数フィールドは表示されません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|NonConstantFieldsShouldNotBeVisible|
|CheckId|CA2211|
|カテゴリ|Microsoft.Usage|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 パブリックまたはプロテクトの静的フィールドは定数もは読み取り専用です。

## <a name="rule-description"></a>規則の説明
 定数でも読み取り専用でもない静的フィールドは、スレッド セーフではありません。 このようなフィールドへのアクセスは、慎重に管理する必要があり、クラス オブジェクトへのアクセスを同期するための高度なプログラミング手法を必要とします。 これらは、困難なスキルについては、マスター、およびそのようなオブジェクトのテストは、独自の課題をもたらすため、静的フィールドは変更されないデータの格納に適しています。 このルールがライブラリに適用されます。アプリケーションでは、フィールドを公開する必要があります。

## <a name="how-to-fix-violations"></a>違反の修正方法
 この規則違反を修正するには、定数または読み取り専用、静的フィールドを確認します。 それができない場合は、基になるフィールドをスレッド セーフなアクセスを管理するスレッド セーフなプロパティなどの代替手段を使用する型を再設計します。 ロックの競合やデッドロックなどの問題は、ライブラリの動作とパフォーマンスに影響がありますに注意してください。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 アプリケーションを開発している場合は、この規則による警告を抑制して、そのため、静的フィールドを含む型へのアクセスを完全に制御があるにも安全です。 ライブラリの設計者は、この規則による警告を抑制しないでください。非定数の静的フィールドを使用するには、開発者にとって困難のライブラリを使用して、適切に使用することができます。

## <a name="example"></a>例
 次の例では、この規則に違反する型を示します。

 [!code-csharp[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/cs/FxCop.Usage.AvoidStaticNonConstants.cs#1)]
 [!code-vb[FxCop.Usage.AvoidStaticNonConstants#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.AvoidStaticNonConstants/vb/FxCop.Usage.AvoidStaticNonConstants.vb#1)]



