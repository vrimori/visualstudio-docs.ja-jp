---
title: "IDebugExpression::Start |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugExpression.Start
apilocation: jscript.dll
helpviewer_keywords: IDebugExpression::Start
ms.assetid: a7af3470-62b5-40f0-987d-63b6b22538b3
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 14d293649e3a6a87c7f594e244378dc2a7e15ac6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="idebugexpressionstart"></a>IDebugExpression::Start
式の評価を開始します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Start(  
   IDebugExpressionCallBack*  pdecb  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pdecb`  
 [in]式の評価が完了したことを示すのコールバック。 このパラメーターが場合`NULL`イベントが発生しないと、クライアントを使用して式の状態をポーリングする必要があります、`QueryIsComplete`です。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|値|説明|  
|-----------|-----------------|  
|`S_OK`|メソッドが成功しました。|  
  
## <a name="remarks"></a>コメント  
 このメソッドは、式の評価を開始します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugExpression::Abort](../../winscript/reference/idebugexpression-abort.md)   
 [IDebugExpression インターフェイス](../../winscript/reference/idebugexpression-interface.md)