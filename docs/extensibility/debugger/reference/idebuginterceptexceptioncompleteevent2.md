---
title: "IDebugInterceptExceptionCompleteEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugInterceptExceptionCompleteEvent2"
helpviewer_keywords: 
  - "IDebugInterceptExceptionCompleteEvent2"
ms.assetid: 8ebc256b-5428-4ed6-a505-6aedc8242b8e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugInterceptExceptionCompleteEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはデバッグ セッションのマネージャー \(SDM\) にデバッグ エンジン \(DE\) によってに完了しますが傍受されたイベントを処理するときに送信されます。  
  
## 構文  
  
```  
IDebugInterceptExceptionCompleteEvent2 : IUnknown  
```  
  
## 実装についてのメモ  
 DE implements 傍受される例外の処理が完了したことを報告します。このインターフェイス  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) のインターフェイスはインターフェイスと同じオブジェクトで実行する必要があります。  SDM は `IDebugEvent2` のインターフェイスへのアクセスに [QueryInterface](/visual-cpp/atl/queryinterface) を使用します。  
  
## 呼び出し元のメモ  
 DE は傍受された例外の完了を報告するにはこのイベント オブジェクトを作成し送信します。  イベントはSDM によって提供される [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のコールバック関数を使用してデバッグ対象のプログラムにアタッチしたときに送信されます。  
  
## Vtable の順序でメソッド  
 `IDebugInterceptExceptionCompleteEvent2` のインターフェイスは以下のメソッドを実装します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetInterceptCookie](../Topic/IDebugInterceptExceptionCompleteEvent2::GetInterceptCookie.md)|処理した例外に関連付けられた一意の値を返します。|  
  
## 解説  
 このイベントは [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) にそのメソッドに傍受された例外の処理が正常に完了すること送信されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)