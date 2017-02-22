---
title: "IDebugEngineCreateEvent2 | Microsoft Docs"
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
  - "IDebugEngineCreateEvent2"
helpviewer_keywords: 
  - "IDebugEngineCreateEvent2 インターフェイス"
ms.assetid: 37c0a841-1c8d-4802-a990-36b54bca3ef7
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngineCreateEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッグ エンジンは \(DE\)デバッグ セッションのマネージャー \(SDM\) に DE のインスタンスが作成されたときにこのインターフェイスを送信します。  
  
## 構文  
  
```  
IDebugEngineCreateEvent2 : IUnknown  
```  
  
## 実装についてのメモ  
 DE implements 正常な動作の一部としてこのインターフェイス。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) のインターフェイスはこのインターフェイス \(インターフェイスにアクセス `IDebugEvent2` SDM を使用 `QueryInterface` のメソッド\) と同じオブジェクトで実行する必要があります。  
  
## 呼び出し元のメモ  
 DE は de\-DE のインスタンスが作成されるとこのイベント オブジェクトを作成し送信します。  イベントはSDM によって提供される [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のコールバック関数を使用してデバッグ対象のプログラムにアタッチしたときに送信されます。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugEngineCreateEvent2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetEngine](../../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)|新しく作成されたデバッグ エンジンを表すオブジェクトを取得します \(DE\)。|  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)