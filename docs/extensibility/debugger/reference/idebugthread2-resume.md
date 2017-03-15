---
title: "IDebugThread2::Resume | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::Resume"
helpviewer_keywords: 
  - "IDebugThread2::Resume"
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

スレッドの実行を再開します。  
  
## 構文  
  
```cpp#  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```c#  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### パラメーター  
 `pdwSuspendCount`  
 \[入力\] 再開操作の後で中断の数を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドが呼び出されるたびに実際に実行が再開される時点で 0 に達するまで中断カウントをデクリメントします。  これは  **スレッド**  のデバッグ ウィンドウで中断数を表示します。  
  
 このメソッドを呼び出すたびに[Suspend](../Topic/IDebugThread2::Suspend.md) のメソッドへの前の呼び出しが必要です。  中断の数は時間を `IDebugThread2::Suspend` のメソッドがここまで呼び出されたかを判定します。  
  
## 参照  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspend](../Topic/IDebugThread2::Suspend.md)