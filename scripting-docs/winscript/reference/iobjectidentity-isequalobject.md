---
title: IObjectIdentity::IsEqualObject |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IObjectIdentity.IsEqualObject
apilocation:
- scrobj.dll
helpviewer_keywords:
- IsEqualObject method
ms.assetid: 78c5c5c2-d299-4036-986c-7c1d87cbe7cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa233e478c83b723b13d19d27dc4b63ee4700bb5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095057"
---
# <a name="iobjectidentityisequalobject"></a>IObjectIdentity::IsEqualObject
オブジェクトが現在のオブジェクトと等しいかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT IsEqualObject(  
  IUnknown*punk  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `punk`  
 [in]現在のオブジェクトと比較するオブジェクトのアドレス。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは `HRESULT` を返します。 有効な値を次の表に示しますが、これ以外にもあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|`S_OK`|オブジェクトが等しいです。|  
|`S_FALSE`|オブジェクトが等しくないです。|  
  
## <a name="remarks"></a>Remarks  
 実装、`IsEqualObject`メソッドが返す`S_OK`オブジェクトが同じ場合にのみです。  
  
## <a name="see-also"></a>関連項目  
 [IObjectIdentity インターフェイス](../../winscript/reference/iobjectidentity-interface.md)