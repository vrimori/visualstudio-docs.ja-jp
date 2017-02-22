---
title: "IDebugProgram2::Step | Microsoft Docs"
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
  - "IDebugProgram2::Step"
helpviewer_keywords: 
  - "IDebugProgram2::Step"
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: 16
caps.handback.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::Step
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

手順を実行します。  
  
> [!NOTE]
>  このメソッドの使用は推奨されていません。  代わりに、[ステップ](../../../extensibility/debugger/reference/idebugprocess3-step.md) メソッドを使用してください。  
  
## 構文  
  
```cpp#  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```c#  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### パラメーター  
 `pThread`  
 \[ステップ イン\] スレッドを表すオブジェクトの [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)。  
  
 `sk`  
 \[入力\] ステップの [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) の種類を指定する列挙体の値。  
  
 `step`  
 \[入力\] ステップの単位を指定する [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) の列挙体からの値 \(ステートメントまたは命令によって\)。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 スレッド間にスレッド同期または通信がある場合はほかのスレッドに特定のスレッドをステップ実行するときに実行する必要があります。  
  
> [!WARNING]
>  この呼び出しを処理している [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) に停止のイベントまたは直接の同期イベント \(\) を送信します ; デバッガーはハングする場合があります。  
  
## 参照  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)