---
title: ': イベント 1713 before または after プレフィックス |Microsoft Docs'
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
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 46ed0ad62d145b7c60c9f20e1a3770016098a236
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589184"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: イベントは、before または after プレフィックスを含むことはできません
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[CA1713: before または after プレフィックス イベントのない](https://docs.microsoft.com/visualstudio/code-quality/ca1713-events-should-not-have-before-or-after-prefix)します。

|||
|-|-|
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|
|CheckId|CA1713|
|カテゴリ|Microsoft.Naming|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 イベントの名前は、'Before' または 'After' で開始します。

## <a name="rule-description"></a>規則の説明
 イベント名は、イベントを発生させるアクションを示す必要があります。 特定のシーケンスで発生する関連イベントに名前を付ける場合、現在時制または過去時制を使用して、アクション シーケンスの相対的な位置を示します。 たとえば、リソースを閉じるときに発生するイベントのペアの名前付け、ときに名前を付けますが '終了' と 'BeforeClose' および 'AfterClose' ではなく ' Closed'。

 名前付け規則では、共通言語ランタイムをターゲットとするライブラリの統一的な名前の付け方が規定されています。 これにより、新しいソフトウェア ライブラリを習得するまでの時間を短縮でき、マネージド コード開発の専門家によってライブラリが開発されたという信頼を顧客に与えることができます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 イベントの名前から、プレフィックスを削除して、現在または過去時制の動詞を使用する名前の変更を検討してください。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 この規則による警告は抑制しないでください。



