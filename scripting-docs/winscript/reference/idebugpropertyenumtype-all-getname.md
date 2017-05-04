---
title: "IDebugPropertyEnumType_All::GetName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugPropertyEnumType_All.GetName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugPropertyEnumType_All::GetName"
ms.assetid: 24bbe4d5-4263-48d0-8e8d-bff957ffcad2
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugPropertyEnumType_All::GetName
`EnumType`の名前を含む BSTR を返します。  
  
## 構文  
  
```  
HRESULT GetName(  
   BSTR*  pname  
);  
```  
  
#### パラメーター  
 `pname`  
 \[入力\] `EnumType`の名前を含む A BSTR。  
  
## 戻り値  
 有効な `HRESULT`、通常 `S_OK`を返します。  
  
## 参照  
 [IDebugPropertyEnumType\_All インターフェイス](../../winscript/reference/idebugpropertyenumtype-all-interface.md)