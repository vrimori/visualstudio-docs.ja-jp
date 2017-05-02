---
title: "JsHasException 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsHasException"
helpviewer_keywords: 
  - "JsHasException 関数"
ms.assetid: ac7da3ce-c746-4154-bbb8-bcb0859a8d5b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsHasException 関数
現在のコンテキストのランタイムが例外状態であるかどうかを指定します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsHasException(  
   _Out_ bool *hasException  
);  
```  
  
#### パラメーター  
 `hasException`  
 現在のコンテキストのランタイムが例外状態であるかどうか。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 \(スクリプトの実行結果として、または変換の失敗などの理由により\) ランタイムに対する呼び出しで例外が発生した場合、ランタイムは "例外状態" になります。 \(例外 API を除く\) ランタイムによって作成されたコンテキストに対するすべての呼び出しは、例外がクリアされるまで、`JsErrorInExceptionState` で失敗します。  
  
 現在のコンテキストのランタイムが例外状態である場合、コールバックがエンジンに戻ると、エンジンが自動的に例外を再スローします。  
  
 アクティブ スクリプトのコンテキストが必要です。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)