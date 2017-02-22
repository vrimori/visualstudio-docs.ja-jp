---
title: "IDebugBreakpointUnboundEvent2 | Microsoft Docs"
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
  - "IDebugBreakpointUnboundEvent2"
helpviewer_keywords: 
  - "IDebugBreakpointUnboundEvent2"
ms.assetid: 6b1e1863-0c64-4d85-8ab9-aface522fdea
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBreakpointUnboundEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはバインド ブレークポイントが読み込まれる \(SDM\) プログラムからアンバ インドされているデバッグ セッションのマネージャーに指示します。  
  
## 構文  
  
```  
IDebugBreakpointUnboundEvent2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンはブレークポイント \(DE\) のサポートの一部としてこのインターフェイスを実装します。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) のインターフェイスはこのインターフェイス \(`IDebugEvent2` のインターフェイスにアクセス [QueryInterface](/visual-cpp/atl/queryinterface) SDM を使用\) と同じオブジェクトで実行する必要があります。  
  
## 呼び出し元のメモ  
 DE はバインド ブレークポイントがアンバ インドこのされたイベント オブジェクトを作成し送信します。  イベントはSDM によって提供される [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のコールバック関数を使用してデバッグ対象のプログラムにアタッチしたときに送信されます。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugBreakpointUnboundEvent2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetBreakpoint](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getbreakpoint.md)|自由になったブレークポイントを取得します。|  
|[GetReason](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2-getreason.md)|ブレークポイントによって対象外の理由を取得します。|  
  
## 解説  
 デバッグ エンジンの DLL またはクラスがアンロードされるときにそのモジュールのコードにバインドされたすべてのブレークポイントでプログラムから解放する必要があります。  `IDebugBreakpointUnboundEvent2` はの非バインド ブレークポイントに送信されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)