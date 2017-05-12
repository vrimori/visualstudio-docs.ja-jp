---
title: "EX_DBGPROP_INFO_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: EX_DBGPROP_INFO_FLAGS
apilocation: scrobj.dll
helpviewer_keywords: 
  - "EX_DBGPROP_INFO_FLAGS"
ms.assetid: ee309dfe-9432-4dff-8756-7a8d677f9dcc
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# EX_DBGPROP_INFO_FLAGS
`ExtendedDebugPropertyInfo` のフィールドを指定するために使用します。  
  
## 構文  
  
```  
enum {  
   EX_DBGPROP_INFO_ID  =0x0100,  
   EX_DBGPROP_INFO_NTYPE  =0x0200,  
   EX_DBGPROP_INFO_NVALUE  =0x0400,  
   EX_DBGPROP_INFO_LOCKBYTES  =0x0800,  
   EX_DBGPROP_INFO_DEBUGEXTPROP  =0x1000  
};  
```  
  
## メンバー  
 EX\_DBGPROP\_INFO\_ID  
 プロパティの識別子を初期化します。  
  
 EX\_DBGPROP\_INFO\_NTYPE  
 プロパティの初期化の型。  
  
 EX\_DBGPROP\_INFO\_NVALUE  
 プロパティの初期化の値。  
  
 EX\_DBGPROP\_INFO\_LOCKBYTES  
 `plb` のフィールドを初期化します。  
  
 EX\_DBGPROP\_INFO\_DEBUGEXTPROP  
 `IDebugExtendedProperty` のインターフェイスを含む `pDebugExtProp` のフィールドを初期化します。  
  
## 参照  
 [ExtendedDebugPropertyInfo 構造体](../../winscript/reference/extendeddebugpropertyinfo-structure.md)   
 [IDebugExtendedProperty インターフェイス](../../winscript/reference/idebugextendedproperty-interface.md)