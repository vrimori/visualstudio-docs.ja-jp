---
title: "IDebugEngineLaunch2::CanTerminateProcess | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngineLaunch2::CanTerminateProcess"
helpviewer_keywords: 
  - "IDebugEngineLaunch2::CanTerminateProcess"
ms.assetid: 7973454d-c957-4123-a0ee-80ebcdbbd2d1
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugEngineLaunch2::CanTerminateProcess
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

プロセスを終了できるかどうかを判定します。  
  
## 構文  
  
```cpp#  
HRESULT CanTerminateProcess (   
   IDebugProcess2* pProcess  
);  
```  
  
```c#  
int CanTerminateProcess (   
   IDebugProcess2 pProcess  
);  
```  
  
#### パラメーター  
 `pProcess`  
 \[入力\] 終了するプロセスを表すオブジェクトの [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コードを返します。  アクセスが拒否されるためエンジンはプロセスを終了できない場合たとえば `S_FALSE` を返します。  
  
## 解説  
 この実際プロセスが終了するにはメソッドの戻り `S_OK` の [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md) その後でメソッドを呼び出すことができます。  
  
## 参照  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [TerminateProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-terminateprocess.md)