---
title: IDebugExpression::GetResultAsDebugProperty |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExpression.GetResultAsDebugProperty
apilocation:
- jscript.dll
helpviewer_keywords:
- IDebugExpression::GetResultAsDebugProperty
ms.assetid: 9075bf2f-d5bb-464e-b6c2-3fa3215e9ae0
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6ce67df5dd55bd8c1ae55bb19fe2a19aed9e40f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727112"
---
# <a name="idebugexpressiongetresultasdebugproperty"></a>IDebugExpression::GetResultAsDebugProperty
デバッグ プロパティおよび操作の戻り値として式の評価の結果を返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetResultAsDebugProperty(  
   HRESULT*          phrResult,  
   IDebugProperty**  ppdp  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `phrResult`  
 [out]操作の戻り値。  
  
 `ppdp`  
 [out]式のデバッグ プロパティです。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
|`E_PENDING`|操作がまだ保留中です。|  
  
## <a name="remarks"></a>コメント  
 このメソッドが戻ると、式の評価の結果、`IDebugProperty`と操作の`HRESULT`します。  
  
 このメソッドが戻る`S_OK`と`phrResult`返します`E_ABORT`場合`Abort`が操作を中止します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugExpression インターフェイス](../../winscript/reference/idebugexpression-interface.md)   
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)