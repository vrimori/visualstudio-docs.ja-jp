---
title: "IDebugProcess3::Continue | Microsoft Docs"
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
  - "IDebugProcess3::Continue"
helpviewer_keywords: 
  - "IDebugProcess3::Continue"
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3::Continue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このプロセスを停止状態から実行する Continues。  の実行前の状態 \(ステップなど\) を再実行するプロセス開始保持されます。  
  
> [!NOTE]
>  このメソッドは [続行](../../../extensibility/debugger/reference/idebugprogram2-continue.md) の代わりに使用されます。  
  
## 構文  
  
```cpp  
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
 \[入力\] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) に実行されるスレッド。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドはに関係なくプロセスをデバッグしたりどのプロセスが停止のイベントが生成されたかこのプロセスで呼び出されます。  実装では実行前を実行する前に停止しないように前回実行状態 \(ステップなど\) は実行を続ける必要があります。  つまり停止した他のプロセスと `Continue` が呼び出されるためこのプロセス内のスレッドが操作手順にして終了すると指定されたスレッドは元の操作手順を実行する必要があります。  
  
 **警告**  は [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)この呼び出しを処理している停止のイベントまたは直接の同期イベントを送信しません \(\); デバッガーはハングする場合があります。  
  
## 参照  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)