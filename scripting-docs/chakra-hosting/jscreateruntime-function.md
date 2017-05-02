---
title: "JsCreateRuntime 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsCreateRuntime"
helpviewer_keywords: 
  - "JsCreateRuntime 関数"
ms.assetid: 92d09b89-6593-4d73-a562-88f9fec10228
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# JsCreateRuntime 関数
新しいランタイムを作成します。  
  
## 構文  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsCreateRuntime(  
   _In_ JsRuntimeAttributes attributes,  
   _In_opt_ JsThreadServiceCallback threadService,  
   _Out_ JsRuntimeHandle *runtime);  
  
// Legacy mode signature  
STDAPI_(JsErrorCode) JsCreateRuntime(  
   _In_ JsRuntimeAttributes attributes,  
   _In_ JsRuntimeVersion version,  
   _In_opt_ JsThreadServiceCallback threadService,  
   _Out_ JsRuntimeHandle *runtime  
);  
```  
  
#### パラメーター  
 `attributes`  
 作成するランタイムの属性。  
  
 `version`  
 作成するランタイムのバージョン。  
  
 `threadService`  
 ランタイムのスレッド サービス。  null を使用できます。  
  
 `runtime`  
 作成するランタイム。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 エッジ モードでは、`version` パラメーターがサポートされていません。  エッジ モードでのこの API の使い方の詳細については、「[Edge エンジンとレガシ エンジンの比較](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md)」を参照してください。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)