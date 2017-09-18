---
title: "IDebugMemoryContext2::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::GetName"
helpviewer_keywords: 
  - "IDebugMemoryContext2::GetName メソッド"
  - "GetName メソッド"
ms.assetid: 8c212556-7d9e-4d68-b2a9-8212f50d0287
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugMemoryContext2::GetName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このコンテキストのユーザー表示できる名前を取得します。  
  
## 構文  
  
```cpp#  
HRESULT GetName(   
   BSTR* pbstrName  
);  
```  
  
```c#  
int GetName(  
   out string pbstrName  
);  
```  
  
#### パラメーター  
 `pbstrName`  
 \[入力\] メモリのコンテキストの名前を返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 メモリのコンテキストの名前はは使用されません。  
  
## 参照  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)