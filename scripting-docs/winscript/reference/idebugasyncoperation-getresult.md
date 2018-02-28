---
title: "IDebugAsyncOperation::GetResult |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IDebugAsyncOperation.GetResult
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::GetResult
ms.assetid: 56d43365-6b12-4213-a97c-953c40d7b7f6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 60181904408010f35fa4d99d182216e665583aab
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugasyncoperationgetresult"></a>IDebugAsyncOperation::GetResult
同期のデバッグ操作から返されたオブジェクト パラメーターと戻り値を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetResult(  
   HRESULT*    phrResult,  
   IUnknown**  ppunkResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `phrResult`  
 [out]操作が完了すると場合、`phrResult`の戻り値は、`IDebugSyncOperation::Execute`です。  
  
 `ppunkResult`  
 [out]操作が完了すると場合、`ppunkResult`操作によって返されるオブジェクトのパラメーターです。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_PENDING`|操作は完了していません。|  
  
## <a name="remarks"></a>コメント  
 かどうか、操作が完了したら、このメソッドが戻る、`HRESULT`オブジェクトからのパラメーターと`IDebugSyncOperation::Execute`です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugAsyncOperation インターフェイス](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)