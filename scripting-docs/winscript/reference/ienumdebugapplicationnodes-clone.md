---
title: "IEnumDebugApplicationNodes::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IEnumDebugApplicationNodes.Clone
apilocation: pdm.dll
helpviewer_keywords: 
  - "IEnumDebugApplicationNodes::Clone"
ms.assetid: 7190954d-e2da-4a84-8e37-81d4d27886a8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugApplicationNodes::Clone
現在の列挙状態と同じ状態を格納する列挙子を作成します。  
  
## 構文  
  
```  
HRESULT Clone(  
   IEnumDebugApplicationNodes**  pperddp  
);  
```  
  
#### パラメーター  
 `pperddp`  
 \[入力\]列挙子の重複する `IEnumDebugApplicationNodes` のインターフェイスを返します。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、現在の列挙子と同じ状態を含む列挙子を作成します。  
  
## 参照  
 [IEnumDebugApplicationNodes インターフェイス](../../winscript/reference/ienumdebugapplicationnodes-interface.md)