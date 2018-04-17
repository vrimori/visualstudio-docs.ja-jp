---
title: 'Ca 1600: アイドル状態のプロセスの優先順位を使わない |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 93255488efa84f553d61aaedb0474c69a4bbb8d0
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="ca1600-do-not-use-idle-process-priority"></a>CA1600: アイドル状態のプロセス優先度を使用しません
|||  
|-|-|  
|TypeName|DoNotUseIdleProcessPriority|  
|CheckId|CA1600|  
|カテゴリ|Microsoft.Mobility|  
|互換性に影響する変更点|あり|  
  
## <a name="cause"></a>原因  
 このルールは、プロセスに設定されているときに発生`ProcessPriorityClass.Idle`です。  
  
## <a name="rule-description"></a>規則の説明  
 プロセス優先順位に Idle を設定しないでください。 持つプロセス`System.Diagnostics.ProcessPriorityClass.Idle`はおよびスタンバイ状態がブロックするには、アイドル状態時に、CPU を占有します。  
  
## <a name="how-to-fix-violations"></a>違反の修正方法  
 プロセス 'éý'`ProcessPriorityClass.BelowNormal`です。  
  
## <a name="when-to-suppress-warnings"></a>警告を抑制する状況  
 アイドル状態のプロセスの優先度が必要し、モビリティに関する考慮事項を安全に無視する場合にのみ、このルールを抑制する必要があります。