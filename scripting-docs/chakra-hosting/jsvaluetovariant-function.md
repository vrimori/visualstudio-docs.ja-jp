---
title: "JsValueToVariant 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsValueToVariant"
helpviewer_keywords: 
  - "JsValueToVariant 関数"
ms.assetid: 070244be-a69d-4b78-971b-69c0579c03cf
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsValueToVariant 関数
JavaScript の値の投影として渡された `VARIANT` を初期化します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsValueToVariant(  
   _In_ JsValueRef object,  
   _Out_ VARIANT *variant  
);  
```  
  
#### パラメーター  
 `object`  
 `VARIANT` として投影する JavaScript の値。  
  
 `variant`  
 投影として初期化される `VARIANT` 構造体へのポインター。  
  
## 戻り値  
  
## 解説  
 投影された JavaScript にオブジェクトを呼び出すために、COM のオートメーション クライアントによって、投影の `VARIANT` を使用できます。  
  
 アクティブ スクリプトのコンテキストが必要です。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)