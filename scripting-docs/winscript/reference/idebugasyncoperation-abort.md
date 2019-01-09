---
title: IDebugAsyncOperation::Abort |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugAsyncOperation.Abort
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugAsyncOperation::Abort
ms.assetid: 232541c6-81b8-4eb7-96a7-a8e5fe087b31
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af8b063f86bd08f293518b1494b41e4f01d61b2c
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54093315"
---
# <a name="idebugasyncoperationabort"></a>IDebugAsyncOperation::Abort
操作をキャンセルします。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT Abort();  
```  
  
#### <a name="parameters"></a>パラメーター  
 このメソッドには、パラメーターはありません。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|S_OK|メソッドが成功しました。|  
|E_NOTIMPL|操作をキャンセルできません。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは通常、応答していない操作をキャンセルするデバッガー スレッド内から呼び出されます。 このメソッドにより、`InProgressAbort`メソッドを`IDebugSyncOperation`呼び出されるオブジェクト。  
  
## <a name="see-also"></a>関連項目  
 [IDebugAsyncOperation インターフェイス](../../winscript/reference/idebugasyncoperation-interface.md)   
 [IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)   
 [IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)