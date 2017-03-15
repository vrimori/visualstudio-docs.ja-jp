---
title: "IDebugProgram3 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProgram3 インターフェイス"
ms.assetid: 4301ba23-c00c-4ce5-8b1e-3f27da312034
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugProgram3
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはプロセスで実行されている表しスレッドの情報を指定してプログラムを [実行](../../../extensibility/debugger/reference/idebugprogram2-execute.md) を拡張します。  
  
## 構文  
  
```  
IDebugProgram3 : IDebugProgram3  
```  
  
## 実装についてのメモ  
 デバッグ エンジン \(DE\) とカスタム ポートの業者はプロセスのプログラムを表すためこのインターフェイスを実装します。  デバッグ セッションのマネージャーは \(SDM\)[Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md) に情報を提供するにはこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) のイベントは新しいプログラムのこのインターフェイスを返します。  このインターフェイスは複数のインターフェイスの多くのメソッドのパラメーターとして使用されます。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugProgram3` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[ExecuteOnThread](../../../extensibility/debugger/reference/idebugprogram3-executeonthread.md)|プログラムを実行します。  スレッドはデバッガーにスレッドが実行するユーザーに表示する情報を提供するために戻ります。|  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 解説  
 プログラムはプロセスは一つ以上のプログラムから成るが特定のランタイム アーキテクチャで実行中のスレッドのコンテナーです。  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [GetProgram](../Topic/IDebugThread2::GetProgram.md)   
 [次へ](../Topic/IEnumDebugPrograms2::Next.md)   
 [イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)   
 [DestroyProgram](../../../extensibility/debugger/reference/idebugengine2-destroyprogram.md)   
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Attach\_V7](../../../extensibility/debugger/reference/idebugprogramnode2-attach-v7.md)