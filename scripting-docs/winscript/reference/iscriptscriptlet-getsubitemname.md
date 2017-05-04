---
title: "IScriptScriptlet::GetSubItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.GetSubItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::GetSubItemName"
ms.assetid: 9ad963fc-9ce8-4b77-92c1-fb90d6307801
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptScriptlet::GetSubItemName
スクリプトレットのオブジェクトのホストの完全修飾名の最後の識別子を返します。  
  
## 構文  
  
```  
HRESULT GetSubItemName(  
   BSTR               *pbstr  
);  
```  
  
#### パラメーター  
 `pbstr`  
 ホストの完全修飾スクリプトレットの名前を複数のレベルがある場合、\[入力\] `pbstr` は、第 2 レベルで識別子のバッファーのアドレスを返します。  
  
 ホストの完全修飾名にスクリプトレット 1 レベルがある場合は、`pbstr` は最初のレベルで識別子のバッファーのアドレスを返します。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
  
## 参照  
 [IScriptScriptlet インターフェイス](../../winscript/reference/iscriptscriptlet-interface.md)