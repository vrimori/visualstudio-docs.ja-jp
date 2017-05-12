---
title: "DBGPROP_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DBGPROP_INFO_FLAGS
apilocation: scrobj.dll
f1_keywords: 
  - "DBGPROP_INFO_FLAGS"
helpviewer_keywords: 
  - "DBGPROP_INFO_FLAGS"
ms.assetid: e9450a21-a802-4c3e-8b3d-8e202f555de1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# DBGPROP_INFO_FLAGS
`DebugPropertyInfo` のフィールドを指定する  
  
## 構文  
  
```  
enum {  
   DBGPROP_INFO_NAME  =0x001,  
   DBGPROP_INFO_TYPE  =0x002,  
   DBGPROP_INFO_VALUE  =0x004,  
   DBGPROP_INFO_FULLNAME  =0x020,  
   DBGPROP_INFO_ATTRIBUTES  =0x008,  
   DBGPROP_INFO_DEBUGPROP  =0x010,  
   DBGPROP_INFO_AUTOEXPAND  =0x8000000  
};  
```  
  
## メンバー  
 DBGPROP\_INFO\_NAME  
 `bstrName` のフィールドを初期化します。  
  
 DBGPROP\_INFO\_TYPE  
 `bstrType` のフィールドを初期化します。  
  
 DBGPROP\_INFO\_VALUE  
 `bstrValue` のフィールドを初期化します。  
  
 DBGPROP\_INFO\_FULLNAME  
 `bstrFullName` のフィールドを初期化します。  
  
 DBGPROP\_INFO\_ATTRIBUTES  
 `dwAttrib` のフィールドを初期化します。  
  
 DBGPROP\_INFO\_DEBUGPROP  
 `IDebugProperty` のインターフェイスを含む `pDebugProp` のフィールドを初期化します。  
  
 DBGPROP\_INFO\_AUTOEXPAND  
 フィールド値がこの型のオブジェクトの自動配置された値を、可能であれば、含めるように指定します。  
  
## 参照  
 [DebugPropertyInfo 構造体](../../winscript/reference/debugpropertyinfo-structure.md)   
 [IDebugProperty インターフェイス](../../winscript/reference/idebugproperty-interface.md)