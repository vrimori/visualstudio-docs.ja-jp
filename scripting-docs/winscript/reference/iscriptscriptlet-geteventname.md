---
title: "IScriptScriptlet::GetEventName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptScriptlet.GetEventName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptScriptlet::GetEventName"
ms.assetid: 548fa650-808e-4c96-8253-5c72e67e8215
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IScriptScriptlet::GetEventName
スクリプトレットに関連付けられたイベントの名前を返します。  
  
## 構文  
  
```  
HRESULT GetEventName(  
   BSTR               *pbstr  
);  
```  
  
#### パラメーター  
 `pbstr`  
 \[入力\] `IScriptScriptlet` のオブジェクトに関連付けられたイベントの名前が格納されるバッファー。  
  
## 戻り値  
 `HRESULT`。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
  
## 参照  
 [IScriptScriptlet インターフェイス](../../winscript/reference/iscriptscriptlet-interface.md)