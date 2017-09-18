---
title: "IDebugProcess3::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::Execute"
helpviewer_keywords: 
  - "IDebugProcess3::Execute"
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess3::Execute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このプロセスを停止状態から実行する Continues。  の実行前の状態 \(ステップなど\) を再度実行するプロセスを開始します。  
  
> [!NOTE]
>  このメソッドは [実行](../../../extensibility/debugger/reference/idebugprogram2-execute.md) の代わりに使用されます。  
  
## 構文  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```c#  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### パラメーター  
 `pThread`  
 \[入力\] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) に実行するスレッド。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 ユーザーが他のプロセスのスレッドが停止状態から実行を開始する場合このメソッドはプロセスに対して呼び出されます。  このメソッドはユーザーが IDE の ENT1ENT \[入力\] メニューの  **開始**  でを選択するときに呼び出されます。  このメソッドの実装ではことができます。プロセスに現在のスレッドの [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) のメソッドを呼び出して簡単です。  
  
> [!WARNING]
>  この呼び出しを処理している [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) に停止のイベントまたは直接の同期イベント \(\) を送信します ; デバッガーはハングする場合があります。  
  
## 参照  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)