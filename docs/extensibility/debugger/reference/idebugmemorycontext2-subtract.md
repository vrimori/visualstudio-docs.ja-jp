---
title: IDebugMemoryContext2::Subtract |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0b57386867d76e4c31181c13336973df3502bf34
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53901861"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
現在のコンテキストから指定された値を減算し、新しいコンテキストを返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Subtract(   
   UINT64                 dwCount,  
   IDebugMemoryContext2** ppMemCxt  
);  
```  
  
```csharp  
int Subtract(  
   ulong                    dwCount,   
   out IDebugMemoryContext2 ppMemCxt  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwCount`  
 [in]デクリメントするメモリのバイト数。  
  
 `ppMemCxt`  
 [out]新しいを返します[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 メモリのコンテキストは、アドレスからの値を減算したコンテキストの新しいインターフェイスを必要とする新しいアドレスを生成するために、アドレスです。  
  
 結果として得られるアドレスがこのコンテキストに関連付けられたメモリ空間の外にある場合でも、新しいコンテキストをこのメソッドを生成することが常にする必要があります。 唯一の例外は、新しいコンテキストのメモリを割り当てることはできませんか場合`ppMemCxt`は (つまり、エラー)、null 値です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)