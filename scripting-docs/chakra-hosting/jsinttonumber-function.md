---
title: "JsIntToNumber 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 1393c4ac-7189-4e9c-8e54-b0e041c22112
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# JsIntToNumber 関数
`int` の値から数値を作成します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsIntToNumber(  
   _In_ int intValue,  
   _Out_ JsValueRef *value  
);  
```  
  
#### パラメーター  
 `intValue`  
 数値に変換する `int` 値。  
  
 `value`  
 新しい数値。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 アクティブ スクリプトのコンテキストが必要です。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)