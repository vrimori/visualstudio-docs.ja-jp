---
title: "IDebugBreakpointEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBreakpointEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointEvent2 インターフェイス"
ms.assetid: 50b3a7a7-331b-42c8-922c-ff3522ebe1da
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugBreakpointEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッグ エンジンは \(DE\)デバッグ セッションにプログラム マネージャー \(SDM\) がブレークポイントで停止する場合はこのインターフェイスを送信します。  
  
## 構文  
  
```  
IDebugBreakpointEvent2 : IUnknown  
```  
  
## 実装についてのメモ  
 DE implements ブレークポイントのサポートの一部としてこのインターフェイス。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) のインターフェイスはこのインターフェイス \(`IDebugEvent2` のインターフェイスにアクセス [QueryInterface](/visual-cpp/atl/queryinterface) SDM を使用\) と同じオブジェクトで実行する必要があります。  
  
## 呼び出し元のメモ  
 DE は 1 文字以上のブレークポイントをプログラムで検出されるとこのイベント オブジェクトを作成し送信します。  イベントはSDM によって提供される [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のコールバック関数を使用してデバッグ対象のプログラムにアタッチしたときに送信されます。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugBreakpointEvent2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[EnumBreakpoints](../../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md)|現在のコード位置で発生したすべてのブレークポイントの列挙子を作成します。|  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)