---
title: "IDebugMemoryContext2::Add | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::Add"
helpviewer_keywords: 
  - "IDebugMemoryContext2::Add メソッド"
  - "Add メソッド"
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugMemoryContext2::Add
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定された値を現在のコンテキストに追加し新しいコンテキストを返します。  
  
## 構文  
  
```cpp#  
HRESULT Add(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```c#  
int Add(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### パラメーター  
 `dwCount`  
 \[入力\] 現在のコンテキストに追加する値。  
  
 `ppMemCxt`  
 \[入力\] [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) の新しいオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 メモリ アドレスのコンテキストはためアドレスに値を追加するには新しいコンテキストのインターフェイスが必要な新しいアドレスを生成します。  
  
 このメソッドはアドレスがこのコンテキストに関連付けられているメモリ空間以外にも新しいコンテキストを常に作り出さなければ必要があります。  ただし唯一の例外はメモリが新しいコンテキストに割り当てることができないか`ppMemCxt` \(エラー\) null 値である場合です。  
  
## 参照  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)