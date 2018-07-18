---
title: Ijsdebugbreakpoint::disable メソッド |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJSDebugBreakPoint.Disable
apilocation:
- jscript9diag.dll
ms.assetid: f6f2889c-c001-4ee5-8e3f-4f36235e4fad
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c53ff133fb07d256d00668e499e5996ac650230f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727842"
---
# <a name="ijsdebugbreakpointdisable-method"></a>IJsDebugBreakPoint::Disable メソッド
ブレークポイントを無効にします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Disable(void);  
```  
  
## <a name="return-value"></a>戻り値  
  
## <a name="remarks"></a>コメント  
 削除されたブレークポイントで呼び出された場合は E_UNEXPECTED を返します。 既に無効になっているブレークポイントで呼び出された場合は S_FALSE を返します。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [IJsDebugBreakPoint インターフェイス](../../winscript/reference/ijsdebugbreakpoint-interface.md)