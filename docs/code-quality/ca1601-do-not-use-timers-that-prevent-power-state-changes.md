---
title: "Ca 1601: 電源の状態の変更を妨げるタイマーを使用しません |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
helpviewer_keywords:
- CA1601
- DoNotUseTimersThatPreventPowerStateChanges
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5fc42c15beda68472f4a980fe96b0055b70a01cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="ca1601-do-not-use-timers-that-prevent-power-state-changes"></a>CA1601: 電源の状態の変更を妨げるタイマーを使用しません
|||  
|-|-|  
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|  
|CheckId|CA1601|  
|カテゴリ|Microsoft.Mobility|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 タイマー間隔に 1 秒あたりの 1 つ以上の時間に発生する設定があります。  
  
## <a name="rule-description"></a>規則の説明  
 ポーリングを避けてください 1 よりも頻繁に発生するタイマーを使用したり秒ごとに 1 回よりもより多くの場合、1 秒あたりの時間。 定期的な動作の頻度が高くなると、CPU のビジー状態が続き、ディスプレイとハード ディスクをオフにする省電力アイドル タイマーに影響を与えます。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 1 秒あたりの 1 つ未満の時間が発生するタイマーの間隔を設定します。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 タイマーの 1 秒あたりの 1 つ以上の時間を発生させることが必要し、モビリティに関する考慮事項を無視しても安全である場合にのみ、このルールを抑制する必要があります。