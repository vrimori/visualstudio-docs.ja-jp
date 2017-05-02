---
title: "JsCreateExternalObject 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsCreateExternalObject"
helpviewer_keywords: 
  - "JsCreateExternalObject 関数"
ms.assetid: 6bcef506-93fb-429b-b06a-a971ff0b71f3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsCreateExternalObject 関数
外部データを格納する新しいオブジェクトを作成します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsCreateExternalObject(  
   _In_opt_ void *data,  
   _In_opt_ JsFinalizeCallback finalizeCallback,  
   _Out_ JsValueRef *object  
);  
```  
  
#### パラメーター  
 `data`  
 オブジェクトが表す外部データ。  null も指定できます。  
  
 `finalizeCallback`  
 オブジェクトの終了処理時のコールバック。  null も指定できます。  
  
 `object`  
 新しいオブジェクト。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 アクティブ スクリプトのコンテキストが必要です。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)