---
title: Ijsdebugdatatarget::readbstr メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugDataTarget.ReadBSTR
apilocation:
- jscript9diag.dll
ms.assetid: 4b571db7-04b9-42a0-9a3e-310ac9d0e659
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: afd216c869cd88a643f68f0abd1fc095a675e24b
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095798"
---
# <a name="ijsdebugdatatargetreadbstr-method"></a>IJsDebugDataTarget::ReadBSTR メソッド
デバッグ対象から BSTR を読み取ります。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT ReadBSTR(  
   UINT64 address,  
   BSTR *pString  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `address`  
 [入力] 読み取り元のアドレス。  
  
 `pString`  
 [出力] デバッグ対象から読み取った BSTR。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="remarks"></a>Remarks  
 アドレスが有効でない場合は E_JsDEBUG_INVALID_MEMORY_ADDRESS を返します。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [IJsDebugDataTarget インターフェイス](../../winscript/reference/ijsdebugdatatarget-interface.md)