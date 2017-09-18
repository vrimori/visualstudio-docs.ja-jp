---
title: "IDebugThread2::SetThreadName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::SetThreadName"
helpviewer_keywords: 
  - "IDebugThread2::SetThreadName"
ms.assetid: fa934121-3f58-44dc-9c30-d3f752e44c8b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugThread2::SetThreadName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

スレッド名を設定します。  
  
## 構文  
  
```cpp#  
HRESULT SetThreadName (   
   LPCOLESTR pszName  
);  
```  
  
```c#  
int SetThreadName (   
   string pszName  
);  
```  
  
#### パラメーター  
 `pszName`  
 \[入力\] スレッドの名前。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 スレッド名を取得するには[GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md) のメソッドを呼び出します。  
  
## 参照  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [GetName](../../../extensibility/debugger/reference/idebugthread2-getname.md)