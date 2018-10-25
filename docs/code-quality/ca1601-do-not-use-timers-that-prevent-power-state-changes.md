---
title: 'CA1601: 電源の状態の変更を妨げるタイマーを使用しません'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9ae36ae1f4af7281c8f32af57fd08cdda6145ba0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49917338"
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: 電源の状態の変更を妨げるタイマーを使用しません

|||
|-|-|
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|
|CheckId|CA1601|
|カテゴリ|Microsoft.Mobility|
|互換性に影響する変更点|あり|

## <a name="cause"></a>原因
 タイマーが、設定を 1 秒あたりの 1 つ以上の時間間隔。

## <a name="rule-description"></a>規則の説明
 ポーリング 1 よりも頻繁に発生するタイマーを使用したり秒ごとに 1 回よりもより多くの場合、1 秒あたりの時間。 定期的な動作の頻度が高くなると、CPU のビジー状態が続き、ディスプレイとハード ディスクをオフにする省電力アイドル タイマーに影響を与えます。

## <a name="how-to-fix-violations"></a>違反の修正方法
 1 秒あたりの 1 つ未満の時間が発生するタイマーの間隔を設定します。

## <a name="when-to-suppress-warnings"></a>警告を抑制します。
 1 秒あたりの 1 つ以上の時間のタイマーを発生させることが必要ですし、モビリティに関する考慮事項を無視しても場合にのみ、このルールを抑制する必要があります。