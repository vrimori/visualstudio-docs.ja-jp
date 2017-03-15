---
title: "IDebugEngineProgram2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineProgram2"
helpviewer_keywords: 
  - "IDebugEngineProgram2 インターフェイス"
ms.assetid: 151003a9-2e4d-4acf-9f4d-365dfa6b9596
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugEngineProgram2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このインターフェイスはマルチスレッド デバッグがサポートされています。  
  
## 構文  
  
```  
IDebugEngineProgram2 : IUnknown  
```  
  
## 実装についてのメモ  
 デバッグ エンジンは複数のスレッドを同時にデバッグをサポートするにはこのインターフェイスを実装します。  このインターフェイスは同じオブジェクトに実装 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) のインターフェイス実装されます。  
  
## 呼び出し元のメモ  
 `IDebugProgram2` のインターフェイスからこのインターフェイスを取得するに [QueryInterface](/visual-cpp/atl/queryinterface) を使用します。  
  
## Vtable の順序でメソッド  
 次の表は `IDebugEngineProgram2` のメソッドを示します。  
  
|メソッド|Description|  
|----------|-----------------|  
|[Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md)|このプログラムで実行しているすべてのスレッドを中断します。|  
|[WatchForThreadStep](../../../extensibility/debugger/reference/idebugengineprogram2-watchforthreadstep.md)|実行を監視実行または停止 \(の場合\)特定のスレッドの発生に表示されます。|  
|[WatchForExpressionEvaluationOnThread](../../../extensibility/debugger/reference/idebugengineprogram2-watchforexpressionevaluationonthread.md)|プログラムが停止しても \(または拒否します\) 式の評価が特定のスレッドに発生するようにします。|  
  
## 解説  
 Visual Studio は [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) のイベントに応じてこのインターフェイスはプログラムの 「スレッドの手順のウォッチ」と 「スレッドの式の評価のウォッチ」ステータスを設定する場合に呼び出します。  [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) はプログラムが停止する必要があるときに呼び出されます ; このメソッドはプログラムにすべてのスレッドを終了する可能性があります。  
  
## 必要条件  
 ヘッダー : msdbg.h  
  
 名前空間 : Microsoft.VisualStudio.Debugger.Interop  
  
 アセンブリ : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 参照  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)