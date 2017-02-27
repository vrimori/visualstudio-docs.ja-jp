---
title: "IDebugProcessEx2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcessEx2::Attach"
helpviewer_keywords: 
  - "IDebugProcessEx2::Attach メソッド"
ms.assetid: f3334ed7-39bf-4d02-a338-36f567b9b287
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugProcessEx2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはセッションはプロセスをデバッグするプロセスを通知します。  
  
## 構文  
  
```cpp#  
HRESULT Attach(   
   IDebugSession2* pSession  
);  
```  
  
```c#  
int Attach(  
   IDebugSession2 pSession  
);  
```  
  
#### パラメーター  
 `pSession`  
 \[出力\] このプロセスにアタッチされているセッションを識別する値。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 `pSession` に渡されるインターフェイスこのプロセスにアタッチされているマネージャーのデバッグ セッションを識別する値として扱う必要があります。; 指定されたインターフェイスのメソッドが機能しません。  
  
## 参照  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)