---
title: "IDebugEventCallback2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEventCallback2"
helpviewer_keywords: 
  - "IDebugEventCallback2"
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugEventCallback2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッグ エンジン \(DE\) によってこのインターフェイスはデバッグ セッションのマネージャー \(SDM\) にデバッグ イベントを送信するために使用されます。  
  
## 構文  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## 実装についてのメモ  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] はデバッグ エンジンのイベントを受け取るにはこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 デバッグ エンジンはSDM が [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)または [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) を呼び出すときにこのインターフェイスを受け取ります。  デバッグ エンジンはSDM に [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) を呼び出してイベントを送信します。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugEventCallback2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|SDM にデバッグ イベント通知を送信します。|  
  
## 解説  
 `IDebugEventCallback2` のインターフェイスを取得することを [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) と [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) を指定しこれに該当せずインターフェイス ポインターは null 値は常にです。  代わりにデバッグ エンジンは呼び出しで受け取る `IDebugEventCallback2` のインターフェイスを [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)[Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)または [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) を使用する必要があります。  
  
 パッケージがマネージ コードの [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) を実行すると<xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> が [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) に渡されるさまざまなインターフェイスで呼び出されることを強くお勧めします。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)