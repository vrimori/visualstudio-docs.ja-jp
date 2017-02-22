---
title: "CA1601: 電源の状態の変更を妨げるタイマーを使用しません | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1601"
  - "DoNotUseTimersThatPreventPowerStateChanges"
helpviewer_keywords: 
  - "CA1601"
  - "DoNotUseTimersThatPreventPowerStateChanges"
ms.assetid: b8028c92-0696-4c54-9773-0028f29bda9a
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1601: 電源の状態の変更を妨げるタイマーを使用しません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseTimersThatPreventPowerStateChanges|  
|CheckId|CA1601|  
|分類|Microsoft.Mobility|  
|互換性に影響する変更点|あり|  
  
## 原因  
 タイマーが、1 秒ごとに複数回発生するように間隔が設定されています。  
  
## 規則の説明  
 1 秒に複数回ポーリングしたり、1 秒に複数回発生するタイマーを使用したりしないでください。  定期的な動作の頻度が高くなると、CPU のビジー状態が続き、ディスプレイとハード ディスクをオフにする省電力アイドル タイマーに影響を与えます。  
  
## 違反の修正方法  
 タイマー間隔を 1 秒に 1 回未満の発生に設定します。  
  
## 警告を抑制する状況  
 1 秒に複数回タイマーを発生させる必要があり、モビリティの考慮事項を無視しても安全な場合のみ、この規則を抑制します。