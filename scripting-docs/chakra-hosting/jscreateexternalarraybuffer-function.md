---
title: "JsCreateExternalArrayBuffer 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4a02aaec-0f67-4bf9-b37c-71cdb1410ca4
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsCreateExternalArrayBuffer 関数
Javascript `ArrayBuffer` オブジェクトを作成して、外部メモリにアクセスします。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsCreateExternalArrayBuffer(  
  _Pre_maybenull_ _Pre_writable_byte_size_(byteLength) void *data,  
  _In_ unsigned int byteLength,  
  _In_opt_ JsFinalizeCallback finalizeCallback,  
  _In_opt_ void *callbackState,  
  _Out_ JsValueRef *result  
);  
  
```  
  
#### パラメーター  
 `data`  
 外部メモリへのポインター。  
  
 `byteLength`  
 外部メモリのバイト数。  
  
 `finalizeCallback`  
 オブジェクトの終了処理時のコールバック。 null も指定できます。  
  
 `callbackState`  
 finalizeCallback に返されるユーザー指定の状態。  
  
 `result`  
 新しい `ArrayBuffer` オブジェクト。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 アクティブ スクリプトのコンテキストが必要です。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)