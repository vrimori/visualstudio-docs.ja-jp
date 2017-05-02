---
title: "IEnumDebugStackFrames::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugStackFrames.Clone
apilocation: jscript.dll
helpviewer_keywords: 
  - "IEnumDebugStackFrames::Clone"
ms.assetid: 9d9e01a3-0be3-4336-832a-f065af388571
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugStackFrames::Clone
現在の列挙状態と同じ状態を格納する列挙子を作成します。  
  
## 構文  
  
```  
HRESULT Clone(  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### パラメーター  
 `ppedsf`  
 \[入力\]列挙子の重複する `IEnumDebugStackFrames`のインターフェイスを返します。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、現在の列挙子と同じ状態を含む列挙子を作成します。  
  
## 参照  
 [IEnumDebugStackFrames インターフェイス](../../winscript/reference/ienumdebugstackframes-interface.md)