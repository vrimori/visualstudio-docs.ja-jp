---
title: "IScriptEntry::SetBody | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetBody
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetBody"
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IScriptEntry::SetBody
`IScriptEntry` のスクリプト ブロックまたは `IScriptScriptlet` のスクリプトレットの本体にあるテキストを設定します。  
  
## 構文  
  
```  
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### パラメーター  
 `psz`  
 \[入力\] `IScriptEntry` のスクリプト ブロックの `psz` は、スクリプトのタグで囲まれたテキストです。  
  
 `IScriptEntry` 関数のブロックの場合、`psz` は、関数本体です。  
  
 `IScriptEntry` \(から派生\) に `IScriptScriptlet` のオブジェクトは、`psz` スクリプトレット スクリプトのテキストです。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
  
## 参照  
 [IScriptEntry インターフェイス](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)