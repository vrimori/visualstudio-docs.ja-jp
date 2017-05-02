---
title: "IDebugExtendedProperty::EnumExtendedMembers | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExtendedProperty.EnumExtendedMembers
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugExtendedProperty::EnumExtendedMembers"
ms.assetid: 27cdb091-da4e-44d2-a631-31ae00468b98
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExtendedProperty::EnumExtendedMembers
拡張プロパティのメンバーを列挙します。  
  
## 構文  
  
```  
HRESULT EnumExtendedMembers(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   IEnumDebugExtendedPropertyInfo**  ppeepi  
);  
```  
  
#### パラメーター  
 `dwFieldSpec`  
 \[入力\]列挙される拡張デバッグのプロパティ構造体のフィールドを決定 EX\_DBGPROP\_INFO\_FLAGS の定数を指定します。  
  
 `nRadix`  
 \[入力\]数値情報の解釈に使用する基数。  
  
 `ppeepi`  
 \[出力\]メンバー プロパティを列挙する `IEnumDebugExtendedPropertyInfo` のインターフェイスを返します。  
  
## 戻り値  
 有効な `HRESULT`、通常 `S_OK`を返します。  
  
## 参照  
 [IDebugExtendedProperty インターフェイス](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX\_DBGPROP\_INFO\_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [ExtendedDebugPropertyInfo 構造体](../../winscript/reference/extendeddebugpropertyinfo-structure.md)