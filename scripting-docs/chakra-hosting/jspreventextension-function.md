---
title: "JsPreventExtension 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsPreventExtension"
helpviewer_keywords: 
  - "JsPreventExtension 関数"
ms.assetid: 8da07e20-d076-4ae4-9fb0-3f3c141518c2
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsPreventExtension 関数
オブジェクトを拡張不能にします。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsPreventExtension(  
   _In_ JsValueRef object  
);  
```  
  
#### パラメーター  
 `object`  
 拡張不能にするオブジェクト。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 アクティブ スクリプトのコンテキストが必要です。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)