---
title: IDebugMemoryBytes2::WriteAt |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4d1d79d88baf9688fe68ff44d59dcd4d19baf9f8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
指定された数の指定したアドレスで始まるメモリのバイトを書き込みます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT WriteAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory  
);  
```  
  
```csharp  
int WriteAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pStartContext`  
 [in][IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)バイトの書き込みを開始する場所を指定するオブジェクト。  
  
 `dwCount`  
 [in]書き込むバイト数。  
  
 `rgbMemory`  
 [in]書き込むバイト。 この配列は以上であると見なされます`dwCount`バイトの列にします。  
  
## <a name="return-value"></a>戻り値  
 成功した場合を返します`S_OK`、それ以外を返します`S_FALSE`か、すべてのバイトが書き込まれるエラー コードを返します (通常`E_FAIL`)。  
  
## <a name="remarks"></a>コメント  
 開始アドレスがこれによって表されるメモリ ウィンドウ内でないかどうかは[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)オブジェクトの書き込みは行われませんと、エラー コードは`E_FAIL`が返されます: 書き込み量のメモリ領域に重なっている場合でもです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)