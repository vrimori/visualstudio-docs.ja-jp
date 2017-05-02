---
title: "IEnumDebugPropertyInfo::Next | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugPropertyInfo.Next
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo::Next"
ms.assetid: 052837ac-1599-49cc-9a5a-ba90f992eeff
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugPropertyInfo::Next
列挙体シーケンスの `DebugPropertyInfo` の構造の指定した数を取得します。  
  
## 構文  
  
```  
HRESULT Next (  
   ULONG celt,  
   DebugPropertyInfo*rgelt,  
   ULONG* pceltFetched  
);  
```  
  
#### パラメーター  
 `celt`  
 \[入力\]取得する `DebugPropertyInfo`の構造体の数。  
  
 `rgelt`  
 \[出力\]取得された `DebugPropertyInfo` の構造体の配列。  
  
 `pceltFetched`  
 \[出力\]実際に取得される `DebugPropertyInfo` の構造体の数を返します。  
  
## 戻り値  
 有効な `HRESULT`、通常 `S_OK`を返します。  
  
## 参照  
 [IEnumDebugPropertyInfo インターフェイス](../../winscript/reference/ienumdebugpropertyinfo-interface.md)   
 [DebugPropertyInfo 構造体](../../winscript/reference/debugpropertyinfo-structure.md)