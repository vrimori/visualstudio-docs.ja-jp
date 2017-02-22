---
title: "モビリティの警告 | Microsoft Docs"
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
  - "vs.codeanalysis.MobilityRules"
helpviewer_keywords: 
  - "マネージ コード分析の警告、モビリティに関する警告"
  - "モビリティに関する警告"
  - "警告、モビリティ"
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# モビリティの警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

モビリティの警告は、効率的な電力の使用法をサポートします。  
  
## このセクションの内容  
  
|規則|説明|  
|--------|--------|  
|[CA1600: アイドル状態のプロセス優先度を使用しません](../code-quality/ca1600-do-not-use-idle-process-priority.md)|プロセス優先順位に Idle を設定しないでください。  System.Diagnostics.ProcessPriorityClass.Idle を設定したプロセスは、CPU を占有するか、そうでない場合はアイドル状態になるため、スタンバイ状態がブロックされます。|  
|[CA1601: 電源の状態の変更を妨げるタイマーを使用しません](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|定期的な動作の頻度が高くなると、CPU のビジー状態が続き、ディスプレイとハード ディスクをオフにする省電力アイドル タイマーに影響を与えます。|