---
title: Ienumjsstackframes::next メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IEnumJsStackFrames.Next
apilocation:
- jscript9diag.dll
ms.assetid: efceb3a1-9239-4f55-9cbb-94670679988b
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f1838d6494311502faf99d86c80e0a74ded4c6e5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092405"
---
# <a name="ienumjsstackframesnext-method"></a>IEnumJsStackFrames::Next メソッド
指定した数のフレームを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT Next(  
   ULONG cFrameCount,  
   JS_NATIVE_FRAME *pFrames,  
   ULONG *pcFetched  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cFrameCount`  
 [入力] 取得するフレームの数。  
  
 `pFrames`  
 [出力] フレームを格納する配列。  
  
 `pcFetched`  
 [出力] 返されたフレーム数。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [IEnumJsStackFrames インターフェイス](../../winscript/reference/ienumjsstackframes-interface.md)