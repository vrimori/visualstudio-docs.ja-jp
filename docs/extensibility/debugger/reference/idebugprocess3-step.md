---
title: "IDebugProcess3::Step | Microsoft Docs"
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
  - "IDebugProcess3::Step"
helpviewer_keywords: 
  - "IDebugProcess3::Step"
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3::Step
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

手順 1 の命令またはステートメントにプロセスを指定します。  
  
> [!NOTE]
>  このメソッドは [ステップ](../../../extensibility/debugger/reference/idebugprogram2-step.md) の代わりに使用されます。  
  
## 構文  
  
```cpp  
HRESULT Step(  
   IDebugThread2* pThread,  
   STEPKIND       sk,  
   STEPUNIT       step,  
);  
```  
  
```c#  
int Step(  
   IDebugThread2 pThread,   
   enum_STEPKIND sk,   
   enum_STEPUNIT step  
);  
```  
  
#### パラメーター  
 `pThread`  
 \[入力\] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) の実行スレッドを表すオブジェクト。  
  
 `sk`  
 \[入力\] [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) 値のいずれか 1 つが。  
  
 `step`  
 \[入力\] [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) 値のいずれか 1 つが。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コードを返します。  
  
## 解説  
 スレッド間にスレッド同期または通信がある場合プロセス内のスレッドは特定のスレッドをステップ実行するときに実行する必要があります。  
  
 **警告**  は [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)この呼び出しを処理している停止のイベントまたは直接の同期イベントを送信しません \(\); デバッガーはハングする場合があります。  
  
## 参照  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [イベント](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)