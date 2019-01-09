---
title: IPerPropertyBrowsing2::GetDisplayString |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetDisplayString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetDisplayString
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4947ebdeac26ae759fb739dd417607dea885ee5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091574"
---
# <a name="iperpropertybrowsing2getdisplaystring"></a>IPerPropertyBrowsing2::GetDisplayString
取得に表示される型は本質的に表示されませんが、返されるテキスト文字列は、プロパティを説明する名前を指定および呼び出し元のユーザー インターフェイスに表示することができます。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dispid`  
 [in]表示名を持つが要求されたプロパティの識別子をディスパッチします。  
  
 `pBstr`  
 [out]ポインター、`BSTR`によって識別されたプロパティの表示名を含む`dispID`します。  
  
## <a name="return-value"></a>戻り値  
 有効な返します`HRESULT`、通常`S_OK`します。  
  
## <a name="remarks"></a>Remarks  
 返される文字列は、プロパティの有効な値ではありません。 プロパティの文字列の表示だけになります。  
  
## <a name="see-also"></a>関連項目  
 [IPerPropertyBrowsing2 インターフェイス 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)