---
title: IDebugProperty::EnumMembers |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.EnumMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::EnumMembers
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07ad47ee8d0232df5f528db659def421475e7b33
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924246"
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
プロパティのメンバーを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGSdwFieldSpec,  
   UINTnRadix,  
   REFIIDrefiid,  
   IEnumDebugPropertyInfo**ppEnum  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwFieldSpec`  
 [in]指定します、`DBGPROP_INFO_FLAGS`列挙のデバッグ プロパティの構造内のフィールド入力するかを決定する定数。  
  
 `nRadix`  
 [in]任意の数値情報を解釈するときに使用する基数。  
  
 `refiid`  
 [in]この IID は、列挙子をフィルター処理するために渡されます。 IID は、のいずれか、`IDebugPropertyEnumType`インターフェイスから継承する`IDebugPropertyEnumType_All`します。  
  
 `ppEnum`  
 [out]返します、`IEnumDebugPropertyInfo`インターフェイス メンバーのプロパティを列挙します。  
  
## <a name="return-value"></a>戻り値  
 有効な返します`HRESULT`、通常`S_OK`します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [IDebugPropertyEnumType_All インターフェイス](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [IEnumDebugPropertyInfo インターフェイス](../../winscript/reference/ienumdebugpropertyinfo-interface.md)