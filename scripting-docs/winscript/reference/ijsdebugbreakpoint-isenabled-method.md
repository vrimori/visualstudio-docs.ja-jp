---
title: Ijsdebugbreakpoint::isenabled メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.IsEnabled
apilocation:
- jscript9diag.dll
ms.assetid: 39b63f49-2a0d-41b7-a2ba-75dcb06251a9
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb7ab887b8e3442a0c38ea403ad43bdea10cdd66
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727892"
---
# <a name="ijsdebugbreakpointisenabled-method"></a>IJsDebugBreakPoint::IsEnabled メソッド
ブレークポイントが有効かどうかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT IsEnabled(  
   BOOL *pIsEnabled  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pIsEnabled`  
 [出力] ブレークポイントが有効な場合は true を、それ以外の場合は false を返します。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="remarks"></a>コメント  
 削除されたブレークポイントで呼び出された場合は E_UNEXPECTED を返します。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [IJsDebugBreakPoint インターフェイス](../../winscript/reference/ijsdebugbreakpoint-interface.md)