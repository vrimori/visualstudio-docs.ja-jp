---
title: IDebugExpression::GetResultAsString |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsString
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsString
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6cee33b5547e30f913407b02a3befd449dda6aeb
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097358"
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
文字列と操作の戻り値として式の評価の結果を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `phrResult`  
 [out]操作の戻り値。  
  
 `pbstrResult`  
 [out]式の評価の結果。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_PENDING`|操作がまだ保留中です。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドは文字列と操作の式の評価の結果を返します`HRESULT`します。  
  
 このメソッドが戻る`S_OK`と`phrResult`返します`E_ABORT`場合`Abort`操作を中止します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugExpression インターフェイス](../../winscript/reference/idebugexpression-interface.md)