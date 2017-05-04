---
title: "JsCreateContext 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsCreateContext"
helpviewer_keywords: 
  - "JsCreateContext 関数"
ms.assetid: aceca043-2c73-4029-a06c-8ad6695109cf
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# JsCreateContext 関数
実行中のスクリプトのスクリプト コンテキストを作成します。  
  
## 構文  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _Out_ JsContextRef *newContext);  
  
// Legacy mode signature  
STDAPI_(JsErrorCode) JsCreateContext(  
   _In_ JsRuntimeHandle runtime,  
   _In_ IDebugApplication *debugApplication,  
   _Out_ JsContextRef *newContext  
);  
```  
  
#### パラメーター  
 `runtime`  
 スクリプト コンテキストを作成するランタイム。  
  
 `debugApplication`  
 デバッグに使用するデバッグ アプリケーション。  このパラメーターは null でもかまいません。その場合、コンテキストでデバッグは無効です。  
  
 `newContext`  
 作成されるスクリプトのコンテキスト。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 各スクリプト コンテキストには、他のすべてのスクリプト コンテキストから分離する独自のグローバル オブジェクトがあります。  
  
 エッジ モードでは、`debugApplication` パラメーターがサポートされていません。  エッジ モードでのこの API の使い方の詳細については、「[Edge エンジンとレガシ エンジンの比較](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md)」を参照してください。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)