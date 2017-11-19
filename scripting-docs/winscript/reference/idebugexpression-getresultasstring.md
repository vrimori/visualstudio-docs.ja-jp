---
title: "IDebugExpression::GetResultAsString |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugExpression.GetResultAsString
apilocation: jscript.dll
helpviewer_keywords: IDebugExpression::GetResultAsString
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 557fe65859d1e3046d64884982070ad233e12559
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressiongetresultasstring"></a>IDebugExpression::GetResultAsString
文字列および操作の戻り値として式の評価の結果を返します。  
  
## <a name="syntax"></a>構文  
  
```  
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
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_PENDING`|操作がまだ保留中です。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは文字列と、操作の式の評価の結果を返します`HRESULT`です。  
  
 このメソッドが戻る`S_OK`と`phrResult`返します`E_ABORT`場合`Abort`が操作を中止します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugExpression インターフェイス](../../winscript/reference/idebugexpression-interface.md)