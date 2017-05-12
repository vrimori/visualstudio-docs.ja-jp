---
title: "JsSetException 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetException"
helpviewer_keywords: 
  - "JsSetException 関数"
ms.assetid: c528793a-2e1b-4ee1-bd2e-e63fd547dc40
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetException 関数
現在のコンテキストのランタイムを例外状態に設定します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsSetException(  
   _In_ JsValueRef exception  
);  
```  
  
#### パラメーター  
 `exception`  
 現在のコンテキストのランタイムに対して設定する JavaScript 例外。  
  
## 戻り値  
 エンジンが例外状態に設定されている場合は `JsNoError`、それ以外の場合は失敗コード。  
  
## 解説  
 現在のコンテキストのランタイムが既に例外状態である場合、この API は `JsErrorInExceptionState` を返します。  
  
 アクティブ スクリプトのコンテキストが必要です。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)