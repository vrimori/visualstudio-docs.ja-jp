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
ms.openlocfilehash: e52a658bd6161542ce909b8294f33d6e4bf140ba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
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