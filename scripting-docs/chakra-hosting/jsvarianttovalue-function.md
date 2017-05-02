---
title: "JsVariantToValue 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsVariantToValue"
helpviewer_keywords: 
  - "JsVariantToValue 関数"
ms.assetid: e8f9eb8b-55b3-4b65-927e-cad5b482edee
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsVariantToValue 関数
`VARIANT` で渡された値の投影である JavaScript 値を作成します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsVariantToValue(  
   _In_ VARIANT *variant,  
   _Out_ JsValueRef *value  
);  
```  
  
#### パラメーター  
 `variant`  
 投影対象の `VARIANT`。  
  
 `value`  
 `VARIANT` の投影である JavaScript 値。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 投影された値は、スクリプトから COM オートメーション オブジェクトを呼び出すために使用できます。  ホストは、COM スレッド規則を適用する必要があります。  
  
 アクティブ スクリプトのコンテキストが必要です。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)