---
title: "IDebugEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEvent2"
helpviewer_keywords: 
  - "IDebugEvent2 インターフェイス"
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスがブレークポイントで停止などの重要なデバッグ情報およびデバッグ メッセージなどの重要情報の両方を伝達するために使用されます。  
  
## 構文  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジン \(DE\) とカスタム ポートの業者は他のすべてのイベント インターフェイスと同じオブジェクトこのインターフェイスを実装します。  
  
## 呼び出し元のメモ  
 適切なイベント インターフェイスを取得するに [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) または [イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md) に提供インターフェイス ID \(IID\) の引数を \(SDM\) 使用して `IDebugEvent2` インターフェイスのデバッグ セッションのマネージャーの呼び出し [QueryInterface](/visual-cpp/atl/queryinterface)。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugEvent2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|このデバッグ イベントの属性を取得します。|  
  
## 解説  
 特定のイベントのインターフェイスは[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) などの IDebugEvent2 インターフェイスから同じ型の別のインターフェイスが `IDebugEvent2` としてオブジェクトとして取得しませんが代わりに実行されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)