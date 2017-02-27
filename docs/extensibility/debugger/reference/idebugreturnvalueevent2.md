---
title: "IDebugReturnValueEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReturnValueEvent2"
helpviewer_keywords: 
  - "IDebugReturnValueEvent2"
ms.assetid: 2daded43-e427-4fbb-a19e-f3834e3723af
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugReturnValueEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはデバッグ セッションのマネージャー \(SDM\) にデバッグ エンジン \(DE\) によって関数のやについての後に送信されます。  
  
## 構文  
  
```  
IDebugReturnValueEvent2 : IUnknown  
```  
  
## 実装についてのメモ  
 DE implements またはステップ イン関数の戻り値を報告します。このインターフェイス  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) のインターフェイスはインターフェイスと同じオブジェクトで実行する必要があります。  SDM は `IDebugEvent2` のインターフェイスへのアクセスに [QueryInterface](/visual-cpp/atl/queryinterface) を使用します。  
  
## 呼び出し元のメモ  
 DE関数の戻り値を報告するにはこのイベント オブジェクトを作成し送信します。  イベントはSDM によって提供される [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のコールバック関数を使用してデバッグ対象のプログラムにアタッチされたときに送信されます。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugReturnValueEvent2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md)|値を関数から返される手順で取得します。|  
  
## 解説  
 関数によって返される値は[GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) を呼び出して取得できます。  戻り値は ENT0ENT \[出力\] ウィンドウに表示されます。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)