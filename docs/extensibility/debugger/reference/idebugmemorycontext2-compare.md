---
title: "IDebugMemoryContext2::Compare |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f96ac8409a5aff3868f33f7ed987a6cc237ba5ea
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
比較フラグ、一致する最初のコンテキストのインデックスを返すことによって示されるように指定した配列内の各コンテキストにメモリ コンテキストを比較します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Compare(   
   CONTEXT_COMPARE        compare,  
   IDebugMemoryContext2** rgpMemoryContextSet,  
   DWORD                  dwMemoryContextSetLen,  
   DWORD*                 pdwMemoryContext  
);  
```  
  
```csharp  
int Compare(  
   enum_CONTEXT_COMPARE   compare,   
   IDebugMemoryContext2[] rgpMemoryContextSet,   
   uint                   dwMemoryContextSetLen,   
   out uint               pdwMemoryContext  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `compare`  
 [in]値、 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)比較の種類を決定する列挙です。  
  
 `rgpMemoryContextSet`  
 [in]参照の配列、 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)と比較するオブジェクト。  
  
 `dwMemoryContextSetLen`  
 [in]内のコンテキストの数、`rgpMemoryContextSet`配列。  
  
 `pdwMemoryContext`  
 [out]比較で一致する最初のメモリ コンテキストのインデックスを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外のエラー コードを返します。 返します`E_COMPARE_CANNOT_COMPARE`場合は 2 つのコンテキストを比較することはできません。  
  
## <a name="remarks"></a>コメント  
 デバッグ エンジン (DE) は、比較のすべての種類をサポートする必要はありませんが、少なくともをサポートする必要があります`CONTEXT_EQUAL`、 `CONTEXT_LESS_THAN`、`CONTEXT_GREATER_THAN`と`CONTEXT_SAME_SCOPE`です。  
  
## <a name="see-also"></a>参照  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)