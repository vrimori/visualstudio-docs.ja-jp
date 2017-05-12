---
title: "ExtendedDebugPropertyInfo 構造体 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ExtendedDebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ExtendedDebugPropertyInfo 構造体"
ms.assetid: f2cf6477-454b-4d13-95da-ae4c90daa175
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ExtendedDebugPropertyInfo 構造体
追加のメンバーを持つ `DebugPropertyInfo` の構造を拡張プロパティを設定する場合は、機能拡張します。  
  
## 構文  
  
```  
typedef struct ExtendedDebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   LPOLESTR  bstrName;  
   LPOLESTR  bstrType;  
   LPOLESTR  bstrValue;  
   LPOLESTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
   DWORD  nDISPID;  
   DWORD  nType;  
   VARIANT  varValue;  
   ILockBytes*  plbValue;  
   IDebugExtendedProperty*  pDebugExtProp;  
};  
```  
  
## メンバー  
 `dwValidFields`  
 フィールドが初期化される場所を指定する列挙型。  
  
 `bstrName`  
 コンテキスト内のプロパティ名。  
  
 `bstrType`  
 書式設定された文字列としてプロパティ型。  
  
 `bstrValue`  
 書式設定された文字列としてプロパティ値。  
  
 `bstrFullName`  
 プロパティの完全名。  
  
 `dwAttrib`  
 デバッグ プロパティのフラグを指定する列挙種別です。  
  
 `pDebugProp`  
 この `ExtendedDebugPropertyInfo`に対応する`IDebugProperty` のオブジェクト。  
  
 `nDISPID`  
 ディスパッチ ID  
  
 `nType`  
 拡張プロパティ型。  
  
 `varValue`  
 バリアントで行うことができる拡張プロパティ値。  
  
 `plbValue`  
 プロパティ値の実際のバイト データ。  
  
 `pDebugExtProp`  
 この `ExtendedDebugPropertyInfo`に対応する`IDebugExtendedProperty` のオブジェクト。  
  
## 参照  
 [DebugPropertyInfo 構造体](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)   
 [IDebugExtendedProperty インターフェイス](../../winscript/reference/idebugextendedproperty-interface.md)   
 [DBGPROP\_ATTRIB\_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)