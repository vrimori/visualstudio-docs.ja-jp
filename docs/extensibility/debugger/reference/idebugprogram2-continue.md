---
title: "IDebugProgram2::Continue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Continue"
helpviewer_keywords: 
  - "IDebugProgram2::Continue"
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugProgram2::Continue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

停止状態からこのプログラムを実行する Continues。  の実行前の状態 \(ステップなど\) を再実行するプログラムの開始時に保持されます。  
  
> [!NOTE]
>  このメソッドの使用は推奨されていません。  代わりに、[続行](../../../extensibility/debugger/reference/idebugprocess3-continue.md) メソッドを使用してください。  
  
## 構文  
  
```cpp#  
HRESULT Continue(   
   IDebugThread2* pThread  
);  
```  
  
```c#  
int Continue(   
   IDebugThread2 pThread  
);  
```  
  
#### パラメーター  
 `pThread`  
 \[入力\] スレッドを表すオブジェクトの [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドはに関係なくプログラムをデバッグまたはプログラムが停止のイベントが生成されたかこのプログラムで呼び出されます。  実装では実行前を実行する前に停止しないように前回実行状態 \(ステップなど\) は実行を続ける必要があります。  つまり停止した他のプログラムやこのメソッドが呼び出されるためプログラムのスレッドが操作手順にして終了するとプログラムは元の操作手順を実行する必要があります。  
  
> [!WARNING]
>  この呼び出しを処理している [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) に停止のイベントまたは直接の同期イベント \(\) を送信します ; デバッガーはハングする場合があります。  
  
## 参照  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)