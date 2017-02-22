---
title: "IDebugPortEvents2 | Microsoft Docs"
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
  - "IDebugPortEvents2"
helpviewer_keywords: 
  - "IDebugPortEvents2 インターフェイス"
ms.assetid: 2c017094-3ba2-4067-83f9-147df1d96bce
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortEvents2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスは特定のポートのリスナーのプロセス \(通常はデバッグ セッションのマネージャー SDM\] または \[デバッグ エンジン\)およびプログラムの作成と破棄されます。  この情報はポートで実行されるプロセスとプログラムのリアルタイムを表示するために使用できます。  
  
## 構文  
  
```  
IDebugPortEvents2 : IUnknown  
```  
  
## 実装についてのメモ  
 Visual Studio では通常プログラムの作成とともに関する通知を受け取るにはこのインターフェイスを実装します。  デバッグ エンジンはこのようなポートのイベントをリッスンするにはこのインターフェイスを実装できます。  
  
## 呼び出し元のメモ  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) のすべてのインターフェイスは <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> のインターフェイスを照会できます。  次 `IDebugPortEvents2` の <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer.FindConnectionPoint%2A> のメソッドは <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> のインターフェイスで <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> インターフェイスを取得します。  最後に<xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> のインターフェイス <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint.Advise%2A> のメソッドは [イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md) のメソッドによってイベントを送信します。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugPortEvents2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[イベント](../../../extensibility/debugger/reference/idebugportevents2-event.md)|ポートのプロセスとプログラムの作成と破棄を表すイベントを送信します。|  
  
## 解説  
 `IDebugPortEvents2` は既にデバッグ プロセスで実行するプログラムのデバッグ SDM によって使用されます。  
  
 ポートのイベントはこのインターフェイスを SDM に渡されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)