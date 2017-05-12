---
title: "IBindEventHandler::BindHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IBindEventHandler.BindHandler
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IBindEventHandler::BindHandler"
ms.assetid: 87909828-2224-4bb1-a6c9-dfe715ac4c9b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IBindEventHandler::BindHandler
オブジェクトにイベントをバインドします。  
  
## 構文  
  
```  
HRESULT BindHandler(  
   LPCOLESTR   pstrEvent,  
   IDispatch*  pdisp  
);  
```  
  
#### パラメーター  
 `pstrEvent`  
 \[入力\]イベントを処理するように指定します。  
  
 `pdisp`  
 \[入力\]オブジェクトのイベントを処理するように指定します。  
  
## 戻り値  
 このメソッドは `HRESULT` を返します。  指定できる値は、に含まれていますが、次の表に、これらはありません。  
  
|値|説明|  
|-------|--------|  
|`S_OK`|メソッドが成功しました。|  
  
## 解説  
 このメソッドは、オブジェクトにイベントをバインドします。  
  
## 参照  
 [IBindEventHandler インターフェイス](../../winscript/reference/ibindeventhandler-interface.md)