---
title: IDebugMemoryBytes2::GetSize |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2::GetSize
helpviewer_keywords:
- IDebugMemoryBytes2::GetSize method
- GetSize method
ms.assetid: dae64c5f-5b54-40c3-b32f-ec3b16c093f7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d8ac99883e2e7d25095a7a9f60eb5b5fe23c531
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55007803"
---
# <a name="idebugmemorybytes2getsize"></a>IDebugMemoryBytes2::GetSize
これによって表されるメモリのバイト単位のサイズを取得[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSize(   
   UINT64* pqwSize  
);  
```  
  
```csharp  
int GetSize(  
   out ulong pqwSize  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pqwSize`  
 [out]バイトのメモリ領域で、サイズを返します。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)