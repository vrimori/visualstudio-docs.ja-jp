---
title: IDebugProgram2::GetMemoryBytes |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::GetMemoryBytes
helpviewer_keywords:
- IDebugProgram2::GetMemoryBytes
ms.assetid: 1cdedb47-caf8-468e-aaf4-163f16afb403
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 217ff277e5d4fb3ba6edbbceb2b3b306f1bbf54e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011768"
---
# <a name="idebugprogram2getmemorybytes"></a>IDebugProgram2::GetMemoryBytes
プログラムによって占有されているメモリのバイト数を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetMemoryBytes(   
   IDebugMemoryBytes2** ppMemoryBytes  
);  
```  
  
```csharp  
int GetMemoryBytes(   
   out IDebugMemoryBytes2 ppMemoryBytes  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppMemoryBytes`  
 [out]返します、 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)プログラムのメモリのバイト数を表すオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`、それ以外のエラー コードを返します。  
  
## <a name="remarks"></a>Remarks  
 メモリのバイト数で表される、 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)メモリとないプログラムが実行されたときに割り当てられたメモリのプログラムのイメージ用オブジェクトです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)