---
title: IDebugAsyncOperation::GetResult |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.GetResult
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::GetResult
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d86e9eb2b934bc6bd4027405d06960cd107f81c1
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087478"
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
同期デバッグ操作から返されたオブジェクトのパラメーターと戻り値を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `phrResult`  
 [out]操作が完了すると場合、`phrResult`の戻り値は、`IDebugSyncOperation::Execute`します。  
  
 `ppunkResult`  
 [out]操作が完了すると場合、`ppunkResult`操作によって返されるオブジェクトのパラメーターです。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_PENDING`|操作が完了していません。|  
  
## <a name="remarks"></a>Remarks  
 かどうか、操作が完了したら、このメソッドが戻る、`HRESULT`オブジェクトからパラメーターと`IDebugSyncOperation::Execute`します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugAsyncOperation インターフェイス](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)