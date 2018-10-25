---
title: IDebugProperty::GetPropertyInfo |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetPropertyInfo
ms.assetid: b201c0c4-bff6-4285-880f-67be90584c5f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c0cdfc48b8e7d5804136e01920b5e8b178628d0a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847371"
---
# <a name="idebugpropertygetpropertyinfo"></a>IDebugProperty::GetPropertyInfo
値を取得、`IDebugProperty`メソッドまたはインデックス付きプロパティを説明します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetPropertyInfo (  
   DBGPROP_INFO_FLAGSdwFields,  
   UINT nRadix,  
   DebugPropertyInfo* pPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwFields`  
 [in]指定します、`DBGPROP_INFO_FLAGS`入力するフィールドを決定する定数、`DebugPropertyInfo`構造体。  
  
 `nRadix`  
 [in]任意の数値情報を書式設定で使用する基数。  
  
 `pPropertyInfo`  
 [out]返します、`DebugPropertyInfo`プロパティを記述する構造体。  
  
## <a name="return-value"></a>戻り値  
 有効な返します`HRESULT`、通常`S_OK`します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [DebugPropertyInfo 構造体](../../winscript/reference/debugpropertyinfo-structure.md)