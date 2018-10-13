---
title: モビリティに関する警告 |Microsoft Docs
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
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6e73864234604f22ec15340740442505fec3e078
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49270076"
---
# <a name="mobility-warnings"></a>モビリティに関する警告
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

モビリティに関する警告は、効率的な電源の使用をサポートします。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|ルール|説明|  
|----------|-----------------|  
|[CA1600: アイドル状態のプロセス優先度を使用しません](../code-quality/ca1600-do-not-use-idle-process-priority.md)|プロセス優先順位に Idle を設定しないでください。 System.Diagnostics.ProcessPriorityClass.Idle を設定したプロセスは、CPU を占有するか、そうでない場合はアイドル状態になるため、スタンバイ状態がブロックされます。|  
|[CA1601: 電源の状態の変更を妨げるタイマーを使用しません](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|定期的な動作の頻度が高くなると、CPU のビジー状態が続き、ディスプレイとハード ディスクをオフにする省電力アイドル タイマーに影響を与えます。|



