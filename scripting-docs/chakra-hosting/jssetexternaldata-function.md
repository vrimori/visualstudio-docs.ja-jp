---
title: "JsSetExternalData 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsSetExternalData"
helpviewer_keywords: 
  - "JsSetExternalData 関数"
ms.assetid: 94e0ad34-67d7-4f7f-88a3-3b057ef5e4b9
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsSetExternalData 関数
外部オブジェクトで外部データを設定します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsSetExternalData(  
   _In_ JsValueRef object,  
   _In_opt_ void *externalData  
);  
```  
  
#### パラメーター  
 `object`  
 外部オブジェクト。  
  
 `externalData`  
 オブジェクトに格納されている外部データ。  外部データがオブジェクトに格納されていない場合は null になることがあります。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 アクティブ スクリプトのコンテキストが必要です。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)