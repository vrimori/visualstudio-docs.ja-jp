---
title: IDebugMemoryBytes2::WriteAt |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c496712c12d25e80677724ca7d80fead0596b146
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51802753"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

指定した数の指定したアドレスで始まるメモリのバイトを書き込みます。  
  
## <a name="syntax"></a>構文  
  
```cpp#  
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
 [in]書き込むバイト数。 この配列は以上であると見なされます`dwCount`サイズ (バイト)。  
  
## <a name="return-value"></a>戻り値  
 成功した場合、返します`S_OK`。 それ以外を返します`S_FALSE`しないすべてのバイトが書き込まれるまたはエラー コードを返します (通常`E_FAIL`)。  
  
## <a name="remarks"></a>Remarks  
 開始アドレスこれによって表されるメモリ ウィンドウ内でないかどうかは[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)オブジェクトの書き込みは行われませんとエラー コードの`E_FAIL`が返されます: メモリ領域に書き込み量が重なっている場合でもです。  
  
## <a name="see-also"></a>関連項目  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

