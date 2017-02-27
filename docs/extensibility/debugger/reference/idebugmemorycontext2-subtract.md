---
title: "IDebugMemoryContext2::Subtract | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMemoryContext2::Subtract"
helpviewer_keywords: 
  - "Subtract メソッド"
  - "IDebugMemoryContext2::Subtract メソッド"
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugMemoryContext2::Subtract
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

指定された値を減算し現在のコンテキストから新しいコンテキストを返します。  
  
## 構文  
  
```cpp#  
HRESULT Subtract(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```c#  
int Subtract(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### パラメーター  
 `dwCount`  
 \[入力\] デクリメントするメモリのバイト数。  
  
 `ppMemCxt`  
 \[入力\] [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) の新しいオブジェクトを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  
  
## 解説  
 メモリ アドレスのコンテキストはためアドレスから値が減算されますが新しいコンテキストのインターフェイスが必要な新しいアドレスを生成します。  
  
 このメソッドはアドレスがこのコンテキストに関連付けられているメモリ空間以外にも新しいコンテキストを常に作り出さなければ必要があります。  ただし唯一の例外はメモリが新しいコンテキストに割り当てることができないか`ppMemCxt` \(エラー\) null 値である場合です。  
  
## 参照  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)