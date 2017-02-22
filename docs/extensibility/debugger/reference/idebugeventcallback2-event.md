---
title: "IDebugEventCallback2::Event | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEventCallback2::Event"
helpviewer_keywords: 
  - "IDebugEventCallback2::Event"
ms.assetid: e5a3345b-d460-4e40-8f5b-3111c56a2ed9
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEventCallback2::Event
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッグ イベント通知を送信します。  
  
## 構文  
  
```cpp#  
HRESULT Event(   
   IDebugEngine2*  pEngine,  
   IDebugProcess2* pProcess,  
   IDebugProgram2* pProgram,  
   IDebugThread2*  pThread,  
   IDebugEvent2*   pEvent,  
   REFIID          riidEvent,  
   DWORD           dwAttrib  
);  
```  
  
```c#  
int Event(   
   IDebugEngine2  pEngine,  
   IDebugProcess2 pProcess,  
   IDebugProgram2 pProgram,  
   IDebugThread2  pThread,  
   IDebugEvent2   pEvent,  
   ref Guid       riidEvent,  
   uint           dwAttrib  
);  
```  
  
#### パラメーター  
 `pEngine`  
 \[出力\] このイベントを送信する [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) デバッグ \(DE\) エンジンを表すオブジェクト。  DE はこのパラメーターを入力する必要があります。  
  
 `pProcess`  
 \[入力\] イベントが発生するプロセスを表すオブジェクトの [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)。  このパラメーターはデバッグ セッションのマネージャー \(SDM\) によって格納されます。  DE はこのパラメーターに null 値を常に渡します。  
  
 `pProgram`  
 \[出力\] このイベントが発生する [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) プログラムを表すオブジェクト。  ほとんどのイベントの場合このパラメーターは null 値ではありません。  
  
 `pThread`  
 \[出力\] このイベントが発生する [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) スレッドを表すオブジェクト。  イベントを行う場合このパラメーターはスタック フレームがこのパラメーターから派生したときに null にすることはできません。  
  
 `pEvent`  
 \[入力\] デバッグ イベントを表す [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) のオブジェクト。  
  
 `riidEvent`  
 \[出力\] によって識別する GUID `pEvent` のパラメーターから取得するイベント インターフェイス。  
  
 `dwAttrib`  
 \[入力\] [複数](../../../extensibility/debugger/reference/eventattributes.md) の列挙体のフラグの組み合わせ。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドを呼び出すときは`dwAttrib` のパラメーターが一致する必要 [GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md) のメソッドから返された値として配置 `pEvent` のパラメーターで渡されるイベント オブジェクト。  
  
 すべてのデバッグ イベントはイベント自体が非同期であるかどうかに関係なく非同期的に送信されます。  DE がこのメソッドを呼び出すと戻り値はイベントが処理されたかどうかは示されませんイベントを受信したかどうかを確認します。  実際ほとんどの場合イベントはこのメソッドは処理されません。  
  
## 参照  
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [複数](../../../extensibility/debugger/reference/eventattributes.md)