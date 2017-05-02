---
title: "JsGetRuntime 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetRuntime"
helpviewer_keywords: 
  - "JsGetRuntime 関数"
ms.assetid: 5b62e940-a885-405a-9fdd-0495fb391b95
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsGetRuntime 関数
コンテキストが属するランタイムを取得します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsGetRuntime(  
   _In_ JsContextRef context,  
   _Out_ JsRuntimeHandle *runtime  
);  
```  
  
#### パラメーター  
 `context`  
 ランタイムを取得するコンテキスト。  
  
 `runtime`  
 コンテキストが属するランタイム。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)