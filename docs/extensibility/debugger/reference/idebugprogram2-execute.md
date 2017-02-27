---
title: "IDebugProgram2::Execute | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::Execute"
helpviewer_keywords: 
  - "IDebugProgram2::Execute"
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugProgram2::Execute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

停止状態からこのプログラムを実行する Continues。  の実行前の状態 \(ステップなど\) を再実行するプログラムを起動します。  
  
> [!NOTE]
>  このメソッドの使用は推奨されていません。  代わりに、[実行](../../../extensibility/debugger/reference/idebugprocess3-execute.md) メソッドを使用してください。  
  
## 構文  
  
```cpp#  
HRESULT Execute(  
   void  
);  
```  
  
```c#  
int Execute();  
```  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 ユーザーが他のプログラムのスレッドが停止状態から実行を開始する場合このメソッドはプログラムで呼び出されます。  このメソッドはユーザーが IDE の ENT1ENT \[入力\] メニューの  **開始**  でを選択するときに呼び出されます。  このメソッドの実装ではことができます。プログラムの現在のスレッドの [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) のメソッドを呼び出して簡単です。  
  
> [!WARNING]
>  この呼び出しを処理している [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) に停止のイベントまたは直接の同期イベント \(\) を送信します ; デバッガーはハングする場合があります。  
  
## 参照  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)