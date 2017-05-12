---
title: "IScriptScriptlet::SetSubItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.SetSubItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::SetSubItemName"
ms.assetid: 619f222f-b4c3-4c7b-9d19-e4e7037343a6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IScriptScriptlet::SetSubItemName
スクリプトレットのオブジェクトのホストの完全修飾名の最後の識別子を設定します。  
  
## 構文  
  
```  
HRESULT SetSubItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### パラメーター  
 `psz`  
 ホストの完全修飾スクリプトレットの名前を複数のレベルがある場合は、`psz` は、第 2 レベルに識別子のバッファーのアドレスです。  
  
 ホストの完全修飾名にスクリプトレット 1 レベルがある場合は、`psz` は最初のレベルに識別子のバッファーのアドレスです。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
  
## 参照  
 [IScriptScriptlet インターフェイス](../../winscript/reference/iscriptscriptlet-interface.md)