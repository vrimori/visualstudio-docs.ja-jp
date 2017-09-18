---
title: "IDebugBinder::GetMemoryContext | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder::GetMemoryContext"
helpviewer_keywords: 
  - "IDebugBinder::GetMemoryContext メソッド"
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugBinder::GetMemoryContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

このメソッドはメモリのコンテキストにおけるオブジェクトの場所またはメモリ アドレスを変換します。  
  
## 構文  
  
```cpp#  
HRESULT GetMemoryContext(   
   IDebugField*           pField,  
   DWORD                  dwConstant,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```c#  
int GetMemoryContext(  
   IDebugField              pField,   
   uint                     dwConstant,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### パラメーター  
 `pField`  
 \[入力\] 検索するオブジェクトを表す [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)。  `NULL` は`dwConstant` を使用します。  
  
 `dwConstant`  
 \[入力\] 0x5000 など設定したメモリ アドレス。  
  
 `ppMemCxt`  
 \[出力\] オブジェクトのアドレスを表す場合はメモリのアドレスを返します [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) のインターフェイス。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 参照  
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)