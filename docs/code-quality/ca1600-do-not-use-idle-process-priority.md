---
title: "Ca 1600: アイドル状態のプロセスの優先順位を使わない |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DoNotUseIdleProcessPriority
- CA1600
helpviewer_keywords:
- CA1600
- DoNotUseIdleProcessPriority
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2d1646cd587295f2854399cfc24603ce1f1910e6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
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