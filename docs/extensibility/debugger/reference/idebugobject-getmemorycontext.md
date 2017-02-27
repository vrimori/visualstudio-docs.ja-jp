---
title: "IDebugObject::GetMemoryContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject::GetMemoryContext"
helpviewer_keywords: 
  - "IDebugObject::GetMemoryContext メソッド"
ms.assetid: 6760a0d3-a898-4e81-b68f-c45c584b225b
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugObject::GetMemoryContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

オブジェクトの値のアドレスを表すメモリのコンテキストを取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetMemoryContext(   
   IDebugMemoryContext2** pContext  
);  
```  
  
```c#  
int GetMemoryContext(  
   ref IDebugMemoryContext2 pContext  
);  
```  
  
#### パラメーター  
 `pContext`  
 \[入力\] [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) のオブジェクトの値を表すオブジェクトのアドレスを返します。  
  
## 戻り値  
 成功した場合は S\_OK; それ以外の場合はエラー コード。  
  
## 解説  
 返されたメモリのコンテキストは [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)このオブジェクトによって表されるように値のアドレスを指定します。  
  
## 参照  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)