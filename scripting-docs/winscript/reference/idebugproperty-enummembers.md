---
title: "IDebugProperty::EnumMembers | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugProperty.EnumMembers
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugProperty::EnumMembers"
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProperty::EnumMembers
プロパティのメンバーを列挙します。  
  
## 構文  
  
```  
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGS dwFieldSpec,  
   UINT nRadix,  
   REFIID refiid,  
   IEnumDebugPropertyInfo** ppEnum  
);  
```  
  
#### パラメーター  
 `dwFieldSpec`  
 \[入力\]列挙されるデバッグのプロパティ構造体のフィールドが入力するかを `DBGPROP_INFO_FLAGS` の定数を指定します。  
  
 `nRadix`  
 \[入力\]数値情報の解釈に使用する基数。  
  
 `refiid`  
 \[出力\]この IID は列挙子をフィルター処理するに渡されます。  IID は `IDebugPropertyEnumType_All`から継承する `IDebugPropertyEnumType` のインターフェイスの 1 つです。  
  
 `ppEnum`  
 \[出力\]メンバー プロパティを列挙する `IEnumDebugPropertyInfo` のインターフェイスを返します。  
  
## 戻り値  
 有効な `HRESULT`、通常 `S_OK`を返します。  
  
## 参照  
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [IDebugPropertyEnumType\_All インターフェイス](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [IEnumDebugPropertyInfo インターフェイス](../../winscript/reference/ienumdebugpropertyinfo-interface.md)