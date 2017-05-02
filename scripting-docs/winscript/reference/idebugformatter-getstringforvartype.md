---
title: "IDebugFormatter::GetStringForVarType | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugFormatter.GetStringForVarType
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugFormatter::GetStringForVarType"
ms.assetid: 1c1a0499-ca57-47e0-8367-fdb4c902bca3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugFormatter::GetStringForVarType
特定の VARTYPE の値を表す文字列を返します。  
  
## 構文  
  
```  
HRESULT GetStringForVarType(  
   VARTYPE    vt,  
   TYPEDESC*  ptdescArrayType,  
   BSTR*      pbstr  
);  
```  
  
#### パラメーター  
 `vt`  
 \[入力\]文字列として表す必要 VARTYPE。  
  
 `ptdescArrayType`  
 \[入力\]型を表す構造体の配列。  
  
 `pbstr`  
 \[入力\] `vt`を表す文字列。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 メソッドは、特定の VARTYPE の値を表す文字列を返します。  
  
## 参照  
 [IDebugFormatter インターフェイス](../../winscript/reference/idebugformatter-interface.md)