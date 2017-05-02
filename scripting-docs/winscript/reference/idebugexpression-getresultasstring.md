---
title: "IDebugExpression::GetResultAsString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugExpression.GetResultAsString
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugExpression::GetResultAsString"
ms.assetid: edadd2ad-9369-4878-bf87-cea15be9f363
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpression::GetResultAsString
文字列演算および演算の戻り値として式の評価の結果を返します。  
  
## 構文  
  
```  
HRESULT GetResultAsString(  
   HRESULT*  phrResult,  
   BSTR*     pbstrResult  
);  
```  
  
#### パラメーター  
 `phrResult`  
 \[入力\]操作の戻り値。  
  
 `pbstrResult`  
 \[入力\]式の評価の結果。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
|`E_PENDING`|操作が保留中です。|  
  
## 解説  
 このメソッドは、文字列と操作の `HRESULT`として式の評価の結果を返します。  
  
 このメソッドは `S_OK` を返し、`Abort` が操作を中止 `phrResult` は `E_ABORT` を返します。  
  
## 参照  
 [IDebugExpression インターフェイス](../../winscript/reference/idebugexpression-interface.md)