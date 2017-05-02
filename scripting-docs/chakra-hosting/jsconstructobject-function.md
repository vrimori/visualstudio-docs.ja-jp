---
title: "JsConstructObject 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsConstructObject"
helpviewer_keywords: 
  - "JsConstructObject 関数"
ms.assetid: b07d2440-db55-4a6a-8376-56b40a8039a1
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsConstructObject 関数
コンストラクターとして関数を呼び出します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsConstructObject(  
   _In_ JsValueRef function,  
   _In_reads_(argumentCount) JsValueRef *arguments,  
   _In_ unsigned short argumentCount,  
   _Out_opt_ JsValueRef *result  
);  
```  
  
#### パラメーター  
 `function`  
 コンストラクターとして呼び出す関数。  
  
 `arguments`  
 呼び出しの引数。  
  
 `argumentCount`  
 関数に渡される引数の数。  
  
 `result`  
 関数の呼び出しから返される値。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 アクティブ スクリプトのコンテキストが必要です。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)