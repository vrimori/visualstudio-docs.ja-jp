---
title: "IDebugEngine2::DestroyProgram | Microsoft Docs"
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
  - "IDebugEngine2::DestroyProgram"
helpviewer_keywords: 
  - "IDebugEngine2::DestroyProgram"
ms.assetid: 0c9e2698-c70f-4770-a7bb-39650e9c3a1f
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine2::DestroyProgram
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定されたプログラムが不規則に終了したことおよびしますがプログラムへのすべての参照を削除しプログラムの破棄イベントを送信することデバッグ エンジン \(DE\) に通知します。  
  
## 構文  
  
```cpp#  
HRESULT DestroyProgram(   
   IDebugProgram2* pProgram  
);  
```  
  
```cpp#  
int DestroyProgram(   
   IDebugProgram2 pProgram  
);  
```  
  
#### パラメーター  
 `pProgram`  
 \[入力\] 終了したプログラムをオンに [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) 表すオブジェクト。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 このメソッドが呼び出された後de\-DE はデバッグ セッションのマネージャー \(SDM\) に従って [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) のイベントを返します。  
  
 このメソッドはを返します \(\) `E_NOTIMPL` デバッグ対象プログラムと同じプロセスにします runs 実行されません。  このメソッドは同じにしますが runs SDM として処理する場合にだけ実行されます。  
  
## 参照  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)