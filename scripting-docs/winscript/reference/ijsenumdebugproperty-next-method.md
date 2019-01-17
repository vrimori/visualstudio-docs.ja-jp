---
title: Ijsenumdebugproperty::next メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsEnumDebugProperty.Next
apilocation:
- jscript9diag.dll
ms.assetid: 9fad1893-483a-440c-88c1-469494212300
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e6b0e3499f9420d42660880f616d2d0873d7a0f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086776"
---
# <a name="ijsenumdebugpropertynext-method"></a>IJsEnumDebugProperty::Next メソッド
このオブジェクトのプロパティを読み取ります。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT Next(  
   ULONG count,  
   IJsDebugProperty **ppDebugProperty,  
   ULONG *pActualCount  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `count`  
 [入力] 読み取るプロパティの数。  
  
 `ppDebugProperty`  
 [出力] プロパティ ブラウザーを表すオブジェクト。  
  
 `pActualCount`  
 [出力] オブジェクトのプロパティの実際の数。  
  
## <a name="return-value"></a>戻り値  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** jscript9diag.h です  
  
## <a name="see-also"></a>関連項目  
 [IJsEnumDebugProperty インターフェイス](../../winscript/reference/ijsenumdebugproperty-interface.md)