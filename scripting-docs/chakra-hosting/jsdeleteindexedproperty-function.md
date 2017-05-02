---
title: "JsDeleteIndexedProperty 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsDeleteIndexedProperty"
helpviewer_keywords: 
  - "JsDeleteIndexedProperty 関数"
ms.assetid: cc876839-2ecd-41a8-82d0-c19b3de944e3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsDeleteIndexedProperty 関数
オブジェクトの指定のインデックス位置にある値を削除します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsDeleteIndexedProperty(  
   _In_ JsValueRef object,  
   _In_ JsValueRef index  
);  
```  
  
#### パラメーター  
 `object`  
 対象となるオブジェクト。  
  
 `index`  
 削除するインデックス。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 アクティブ スクリプトのコンテキストが必要です。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)