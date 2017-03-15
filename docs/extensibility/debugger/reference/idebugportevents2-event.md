---
title: "IDebugPortEvents2::Event | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortEvents2::Event"
helpviewer_keywords: 
  - "IDebugPortEvents2::Event"
ms.assetid: 5cc813f7-04a1-4462-9ea7-fbddcf0e0143
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# IDebugPortEvents2::Event
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはポートのプロセスとプログラムの作成と破棄を示すイベントを送信します。  
  
## 構文  
  
```cpp#  
HRESULT Event(  
   IDebugCoreServer2* pServer,  
   IDebugPort2*       pPort,  
   IDebugProcess2*    pProcess,  
   IDebugProgram2*    pProgram,  
   IDebugEvent2*      pEvent,  
   REFIID             riidEvent  
);  
```  
  
```c#  
int Event(  
   IDebugCoreServer2 pServer,   
   IDebugPort2       pPort,   
   IDebugProcess2    pProcess,   
   IDebugProgram2    pProgram,   
   IDebugEvent2      pEvent,   
   ref Guid          riidEvent  
);  
```  
  
#### パラメーター  
 `pMachine`  
 \[入力\] デバッグ サーバーを表す [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) のオブジェクト \(一つのイベントが発生した [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] のインスタンスごとに 1 回です。  
  
 `pPort`  
 \[入力\] イベントが発生した [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) のポートを表すオブジェクト。  
  
 `pProcess`  
 \[入力\] イベントが発生したプロセスを表すオブジェクトの [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)。  
  
 `pProgram`  
 \[入力\] イベントが発生した [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) プログラムを表すオブジェクト。  
  
 `pEvent`  
 \[入力\] イベントを識別する [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) のオブジェクト。  できるイベントは次のとおりです。:  
  
-   [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)  
  
-   [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)  
  
-   [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
-   [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)  
  
 `riidEvent`  
 \[入力\] イベントの GUID。  イベントがこのメソッドを呼び出す前に [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) にキャストされるためこの識別子はのイベントが送信されるかを確認しやすくなります。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)