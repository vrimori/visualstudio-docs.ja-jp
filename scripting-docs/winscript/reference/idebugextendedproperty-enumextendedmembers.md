---
title: IDebugExtendedProperty::EnumExtendedMembers |Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExtendedProperty.EnumExtendedMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugExtendedProperty::EnumExtendedMembers
ms.assetid: 27cdb091-da4e-44d2-a631-31ae00468b98
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 400145cf3981b7266a796f66576eb12f979d2750
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949840"
---
# <a name="idebugextendedpropertyenumextendedmembers"></a>IDebugExtendedProperty::EnumExtendedMembers
拡張プロパティのメンバーを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumExtendedMembers(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   IEnumDebugExtendedPropertyInfo**  ppeepi  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dwFieldSpec`  
 [in]情報を格納する、列挙内のフィールドの拡張プロパティの構造体のデバッグを決定する EX_DBGPROP_INFO_FLAGS 定数を指定します。  
  
 `nRadix`  
 [in]任意の数値情報を解釈するときに使用する基数。  
  
 `ppeepi`  
 [out]返します、`IEnumDebugExtendedPropertyInfo`インターフェイス メンバーのプロパティを列挙します。  
  
## <a name="return-value"></a>戻り値  
 有効な返します`HRESULT`、通常`S_OK`します。  
  
## <a name="see-also"></a>関連項目  
 [IDebugExtendedProperty インターフェイス](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX_DBGPROP_INFO_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [ExtendedDebugPropertyInfo 構造体](../../winscript/reference/extendeddebugpropertyinfo-structure.md)