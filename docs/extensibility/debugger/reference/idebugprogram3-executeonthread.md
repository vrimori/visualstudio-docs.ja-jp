---
title: "IDebugProgram3::ExecuteOnThread | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProgram3::ExecuteOnThread"
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram3::ExecuteOnThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

デバッガーでプログラムを実行します。  スレッドはデバッガーにスレッドがユーザーとプログラムを実行する表示する情報を提供するために戻ります。  
  
## 構文  
  
```cpp#  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```c#  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### パラメーター  
 `pThread`  
 \[入力\] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) のオブジェクト。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 デバッガーが停止した後で実行を再開するには3 とおりの方法があります :  
  
-   : 実行します。前の手順をキャンセルするには次のブレークポイントまでの実行します。  
  
-   ステップ : 古いステップをキャンセルし新しいステップが完了するまで実行します。  
  
-   continue: 再度実行し前の手順でアクティブのままにします。  
  
 `ExecuteOnThread` に渡されたスレッドはキャンセルする手順を決定する場合に便利です。  スレッドがわからない場合はキャンセルを実行するすべてのステップ実行します。  スレッドの知識によってのみアクティブなスレッドの手順を取り消す必要があります。  
  
## 参照  
 [実行](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)