---
title: "JsEquals 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsEquals"
helpviewer_keywords: 
  - "JsEquals 関数"
ms.assetid: 8377a7b6-12ff-43e4-8cc8-5a5a198a168b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsEquals 関数
2 つの JavaScript 値が等しいかどうかを比較します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsEquals(  
   _In_ JsValueRef object1,  
   _In_ JsValueRef object2,  
   _Out_ bool *result  
);  
```  
  
#### パラメーター  
 `object1`  
 比較する最初のオブジェクト。  
  
 `object2`  
 比較する 2 番目のオブジェクト。  
  
 `result`  
 値が等しいかどうか。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 この関数は、Javascript の `==` 演算子と等価です。  
  
 アクティブ スクリプトのコンテキストが必要です。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)