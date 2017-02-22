---
title: "プログラムの終了 | Microsoft Docs"
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
  - "プログラムの終了イベント"
  - "[デバッグの SDK] のデバッグ、プログラムの終了"
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# プログラムの終了
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

次の 1 とおりのスレッドで一つのプログラムの終了について説明します。  
  
## 終了の手順  
  
1.  DE sends 有効な [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) の [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)。  
  
2.  DE sends 有効な [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) の [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)。  
  
 IDE はデザイン モードに入ります。  ポートからプログラムを削除するデバッグ エンジンまたはランタイム環境では [IDebugPortNotify2:: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md)。  
  
## 参照  
 [デバッガー イベントの呼び出し](../../extensibility/debugger/calling-debugger-events.md)