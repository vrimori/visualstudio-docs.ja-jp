---
title: "JsGetAndClearException 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsGetAndClearException"
helpviewer_keywords: 
  - "JsGetAndClearException 関数"
ms.assetid: 6aec8a88-41ee-47f6-b5f4-32f3cae6bb7b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsGetAndClearException 関数
現在のコンテキストのランタイムを例外状態にした例外を返し、そのランタイムの例外状態をリセットします。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsGetAndClearException(  
   _Out_ JsValueRef *exception  
);  
```  
  
#### パラメーター  
 `exception`  
 現在のコンテキストでランタイム例外。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 現在のコンテキストのランタイムが例外状態でない場合、この API は `JsErrorInvalidArgument` を返します。  ランタイムが無効である場合は、スクリプトが終了したことを示す例外を返しますが、例外はクリアしません \(`JsEnableRuntimeExecution` を使用してランタイムを再度有効化すると、例外はクリアされます\)。  
  
 アクティブ スクリプトのコンテキストが必要です。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)