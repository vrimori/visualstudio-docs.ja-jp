---
title: "IDebugBreakpointRequest2 | Microsoft Docs"
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
  - "IDebugBreakpointRequest2"
helpviewer_keywords: 
  - "IDebugBreakpointRequest2 インターフェイス"
ms.assetid: 01ac4013-96f9-4235-b289-f55f9e99558f
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointRequest2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはブレークポイントの型を作成しバインドするために必要な情報を表します。  
  
## 構文  
  
```  
IDebugBreakpointRequest2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ セッションのマネージャーは \(SDM\)このインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 デバッグ エンジンは[CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md) \(DE\) の呼び出しに保留中のブレークポイントを作成するにはこのインターフェイスを受け取ります。  [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md) の呼び出しは de\-DE からこのインターフェイスを取得できます。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugBreakpointRequest2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetLocationType](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getlocationtype.md)|このブレークポイントの要求のブレークポイント位置の型を取得します。|  
|[GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)|このブレークポイントの要求を記述したブレークポイントの要求された情報を取得します。|  
  
## 解説  
 デバッグ対象が読み込まれた後[バインド](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) の呼び出しはプログラムの要求された位置に保留中のブレークポイントをバインドします。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [CreatePendingBreakpoint](../../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)   
 [GetBreakpointRequest](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-getbreakpointrequest.md)   
 [バインド](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)