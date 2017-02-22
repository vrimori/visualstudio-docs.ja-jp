---
title: "IDebugMemoryContext2::Compare | Microsoft Docs"
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
  - "IDebugMemoryContext2::Compare"
helpviewer_keywords: 
  - "IDebugMemoryContext2::Compare メソッド"
  - "Compare メソッド"
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugMemoryContext2::Compare
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

表示方法を指定された配列の各コンテキストがメモリのコンテキストを比較して一致する最初のコンテキストのインデックスを返すフラグを比較します。  
  
## 構文  
  
```cpp#  
HRESULT Compare(   
   CONTEXT_COMPARE        compare,  
   IDebugMemoryContext2** rgpMemoryContextSet,  
   DWORD                  dwMemoryContextSetLen,  
   DWORD*                 pdwMemoryContext  
);  
```  
  
```c#  
int Compare(  
   enum_CONTEXT_COMPARE   compare,   
   IDebugMemoryContext2[] rgpMemoryContextSet,   
   uint                   dwMemoryContextSetLen,   
   out uint               pdwMemoryContext  
);  
```  
  
#### パラメーター  
 `compare`  
 \[入力\] 比較の種類を決定 [CONTEXT\_COMPARE](../../../extensibility/debugger/reference/context-compare.md) の列挙体の値。  
  
 `rgpMemoryContextSet`  
 \[入力\] [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) への参照の配列はとして比較します。  
  
 `dwMemoryContextSetLen`  
 \[入力\] 配列の `rgpMemoryContextSet` コンテキストの数。  
  
 `pdwMemoryContext`  
 \[入力\] 比較を満たす最初のメモリのコンテキストのインデックスを返します。  
  
## 戻り値  
 正常に終了した場合戻り `S_OK`; それ以外の場合はエラー コード。  2 個のコンテキストを比較する場合 `E_COMPARE_CANNOT_COMPARE` を返します。  
  
## 解説  
 デバッグ エンジンは比較 \(DE\) のすべての型をサポートする必要はありません `CONTEXT_EQUAL`少なくとも `CONTEXT_LESS_THAN``CONTEXT_GREATER_THAN` と `CONTEXT_SAME_SCOPE` をサポートする必要があります。  
  
## 参照  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT\_COMPARE](../../../extensibility/debugger/reference/context-compare.md)