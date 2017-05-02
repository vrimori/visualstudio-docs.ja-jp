---
title: "IScriptScriptlet::GetSimpleEventName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet. GetSimpleEventName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::GetSimpleEventName"
ms.assetid: 012eb555-b26c-4248-bbcc-fc30e6f2b308
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IScriptScriptlet::GetSimpleEventName
スクリプトレットに関連付けられている単純なイベントの名前を返します。  これは空白文字を含まない 1 語の名前です。  
  
## 構文  
  
```  
HRESULT GetSimpleEventName(  
   BSTR               *pbstr  
);  
```  
  
#### パラメーター  
 `pbstr`  
 \[入力\] `IScriptScriptlet` のオブジェクトに関連付けられている単純なイベントの名前が格納されるバッファー。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
  
## 参照  
 [IScriptScriptlet インターフェイス](../../winscript/reference/iscriptscriptlet-interface.md)