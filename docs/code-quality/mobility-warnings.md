---
title: モビリティに関する警告
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- vs.codeanalysis.MobilityRules
helpviewer_keywords:
- managed code analysis warnings, mobility warnings
- mobility warnings
- warnings, mobility
ms.assetid: 9808054c-593b-4fc3-92cc-1fc45f41569c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2125f8fc674c91d5bbb301c13a3a898b79e174a8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889964"
---
# <a name="mobility-warnings"></a>モビリティに関する警告
モビリティに関する警告は、効率的な電源の使用をサポートします。

## <a name="in-this-section"></a>このセクションの内容

|ルール|説明|
|----------|-----------------|
|[CA 1600:アイドル状態のプロセスの優先順位を使用しないでください。](../code-quality/ca1600-do-not-use-idle-process-priority.md)|プロセス優先順位に Idle を設定しないでください。 System.Diagnostics.ProcessPriorityClass.Idle を設定したプロセスは、CPU を占有するか、そうでない場合はアイドル状態になるため、スタンバイ状態がブロックされます。|
|[CA 1601:電源状態の変更を妨げるタイマーを使用しないでください。](../code-quality/ca1601-do-not-use-timers-that-prevent-power-state-changes.md)|定期的な動作の頻度が高くなると、CPU のビジー状態が続き、ディスプレイとハード ディスクをオフにする省電力アイドル タイマーに影響を与えます。|