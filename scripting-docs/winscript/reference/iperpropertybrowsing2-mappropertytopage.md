---
title: IPerPropertyBrowsing2::MapPropertyToPage |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.MapPropertyToPage
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::MapPropertyToPage
ms.assetid: e6418a8e-500b-42e1-9b5a-52e6f7567f99
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: caa1b028627eaec0b3c2b7d9a73ca220111603a0
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938046"
---
# <a name="iperpropertybrowsing2mappropertytopage"></a>IPerPropertyBrowsing2::MapPropertyToPage
このプロパティの編集に使用できるプロパティ ページの CLSID を返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT MapPropertyToPage(  
   DISPID  dispid,  
   CLSID*  pClsidPropPage  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dispid`  
 [in]目的のプロパティの識別子をディスパッチします。  
  
 `pClsidPropPage`  
 [out]プロパティに関連付けられたプロパティ ページを識別する CLSID へのポインター。 このメソッドが失敗した場合、*`pClsidPropPage` CLSID_ に設定されます。  
  
## <a name="return-value"></a>戻り値  
 有効な返します`HRESULT`、通常`S_OK`します。  
  
## <a name="see-also"></a>関連項目  
 [IPerPropertyBrowsing2 インターフェイス 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)