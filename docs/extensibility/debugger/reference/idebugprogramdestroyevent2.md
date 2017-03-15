---
title: "IDebugProgramDestroyEvent2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramDestroyEvent2"
helpviewer_keywords: 
  - "IDebugProgramDestroyEvent2"
ms.assetid: ddf127ca-c4a5-4071-90ca-68faf2f57dbd
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgramDestroyEvent2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはデバッグ セッションのマネージャー \(SDM\) にデバッグ エンジン \(DE\) によってプログラムが完了まで実行されたときに送信されます。  
  
## 構文  
  
```  
IDebugProgramDestroyEvent2 : IUnknown  
```  
  
## 実装についてのメモ  
 DE またはカスタム ポートの業者はプログラムが終了した実行およびデバッグに対して使用可能であることを報告するためにこのインターフェイスは。  [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) のインターフェイスはインターフェイスと同じオブジェクトで実行する必要があります。  SDM は `IDebugEvent2` のインターフェイスへのアクセスに [QueryInterface](/visual-cpp/atl/queryinterface) を使用します。  
  
## 呼び出し元のメモ  
 DE またはカスタム ポートの業者はプログラムの終了を報告するためこのイベント オブジェクトを作成し送信します。  DE sends デバッグ対象のプログラムにアタッチするときの SDM によって提供される [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) のコールバック関数を使用してこのイベント。  カスタム ポートの業者は [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) のインターフェイスを使用してこのイベントを送信します。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugProgramDestroyEvent2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[GetExitCode](../Topic/IDebugProgramDestroyEvent2::GetExitCode.md)|プログラムの終了コードを取得します。|  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [コア インターフェイス](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)