---
title: "IEnumDebugExtendedPropertyInfo::Skip | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugExtendedPropertyInfo.Skip
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IEnumDebugExtendedPropertyInfo::Skip"
ms.assetid: a0b4a9fc-e122-482b-9384-b83c460b61fe
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugExtendedPropertyInfo::Skip
列挙体シーケンスの `ExtendedDebugPropertyInfo` の構造の指定した数の要素をスキップします。  
  
## 構文  
  
```  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
#### パラメーター  
 `celt`  
 \[スキップ\]列挙体シーケンスの `ExtendedDebugPropertyInfo` の構造体の数。  
  
## 戻り値  
 有効な `HRESULT`、通常 `S_OK`を返します。  `celt` が返された `S_FALSE` と列挙子である要素の数より大きい場合は列挙の終了時に設定すると、現在の要素のポインター。  
  
## 参照  
 [IEnumDebugExtendedPropertyInfo インターフェイス](../../winscript/reference/ienumdebugextendedpropertyinfo-interface.md)   
 [ExtendedDebugPropertyInfo 構造体](../../winscript/reference/extendeddebugpropertyinfo-structure.md)