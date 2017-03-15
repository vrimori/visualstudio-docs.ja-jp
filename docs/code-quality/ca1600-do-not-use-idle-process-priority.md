---
title: "CA1600: アイドル状態のプロセス優先度を使用しません | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DoNotUseIdleProcessPriority"
  - "CA1600"
helpviewer_keywords: 
  - "CA1600"
  - "DoNotUseIdleProcessPriority"
ms.assetid: 9b0d073b-78b6-41be-8ef3-14692a735283
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1600: アイドル状態のプロセス優先度を使用しません
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseIdleProcessPriority|  
|CheckId|CA1600|  
|分類|Microsoft.Mobility|  
|互換性に影響する変更点|あり|  
  
## 原因  
 この規則は、プロセスが `ProcessPriorityClass.Idle` に設定されたために適用されています。  
  
## 規則の説明  
 プロセス優先順位に Idle を設定しないでください。  `System.Diagnostics.ProcessPriorityClass.Idle` を設定したプロセスは、CPU を占有するか、そうでない場合はアイドル状態になるため、スタンバイ状態がブロックされます。  
  
## 違反の修正方法  
 プロセスに `ProcessPriorityClass.BelowNormal` を設定します。  
  
## 警告を抑制する状況  
 この規則を抑制できるのは、Idle のプロセス優先順位が必要であり、モビリティの問題を無視しても安全な場合のみです。