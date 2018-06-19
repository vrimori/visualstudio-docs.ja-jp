---
title: IDebugProperty::EnumMembers |Microsoft ドキュメント
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
ms.openlocfilehash: 9cb57f2609fcd9a80e2a9e0dfd63637e6f700047
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24727542"
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
 [in]指定します、`DBGPROP_INFO_FLAGS`を入力するプロパティの列挙されたデバッグ構造体のフィールドを決定する定数。  
  
 `nRadix`  
 [in]任意の数値情報を解釈するときに使用する基数。  
  
 `refiid`  
 [in]この IID は、列挙子をフィルター処理に渡されます。 IID はの 1 つ、`IDebugPropertyEnumType`インターフェイスから継承する`IDebugPropertyEnumType_All`です。  
  
 `ppEnum`  
 [out]返します、`IEnumDebugPropertyInfo`メンバー プロパティを列挙するインターフェイスです。  
  
## <a name="return-value"></a>戻り値  
 有効な返します`HRESULT`通常`S_OK`です。  
  
## <a name="see-also"></a>関連項目  
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [IDebugPropertyEnumType_All インターフェイス](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [IEnumDebugPropertyInfo インターフェイス](../../winscript/reference/ienumdebugpropertyinfo-interface.md)