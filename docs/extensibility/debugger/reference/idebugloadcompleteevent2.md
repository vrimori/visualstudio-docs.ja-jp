---
title: "IDebugLoadCompleteEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugLoadCompleteEvent2"
helpviewer_keywords: 
  - "IDebugLoadCompleteEvent2"
ms.assetid: 37eb7360-28e9-4273-862a-4c17f22af690
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugLoadCompleteEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはデバッグ セッションのマネージャー \(SDM\) にデバッグ エンジン \(DE\) によってプログラムが読み込まれるとコードが実行される前に送信されます。  
  
## 構文  
  
```  
IDebugLoadCompleteEvent2 : IUnknown  
```  
  
## 実装についてのメモ  
 DE implements プログラムが正常に読み込まれたことを報告します。このインターフェイス  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) のインターフェイスはインターフェイスと同じオブジェクトで実行する必要があります。  SDM は `IDebugEvent2` のインターフェイスへのアクセスに [QueryInterface](/visual-cpp/atl/queryinterface) を使用します。  
  
## 呼び出し元のメモ  
 DE はプログラムが正常に読み込まれたことを報告するためこのイベント オブジェクトを作成し送信します。  イベントはSDM によって提供される [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のコールバック関数を使用してデバッグ対象のプログラムにアタッチしたときに送信されます。  
  
## 解説  
 このイベントは停止のイベントではイベント属性の `EVENT_STOPPING` フラグが設定されている必要があります。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)