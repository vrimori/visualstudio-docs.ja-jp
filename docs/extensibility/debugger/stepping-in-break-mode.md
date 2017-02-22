---
title: "中断モードでのステップ実行 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "中断モードでは、ステップ実行"
  - "中断モードでのステップ実行"
  - "[デバッグの SDK] のデバッグ、中断モードでのステップ実行"
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# 中断モードでのステップ実行
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

次にデバッガーが中断モードでコードを通過しなかった場合があるときに発生するプロセスについて説明します :  
  
## 手順の手順  
  
1.  手順を実行する [STEPKIND](../../extensibility/debugger/reference/stepkind.md) と [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) の引数では [IDebugProgram2:: 手順](../../extensibility/debugger/reference/idebugprogram2-step.md)。  
  
2.  ステップが完了すると停止のイベントとして [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) を送信します。  
  
## 参照  
 [デバッガー イベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)