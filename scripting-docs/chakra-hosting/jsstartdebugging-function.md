---
title: "JsStartDebugging 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsStartDebugging"
helpviewer_keywords: 
  - "JsStartDebugging 関数"
ms.assetid: c48ba02d-6d47-466f-a970-02f087d525f3
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# JsStartDebugging 関数
現在のコンテキストでデバッグを開始します。  
  
## 構文  
  
```  
// Edge mode signature  
STDAPI_(JsErrorCode) JsStartDebugging();  
  
// Legacy mode signature  
STDAPI_(JsErrorCode)  JsStartDebugging(  
   _In_ IDebugApplication *debugApplication  
);  
```  
  
#### パラメーター  
 `debugApplication`  
 デバッグに使用するデバッグ アプリケーション。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 ホストは、この API を呼び出す前に少なくとも一度 `COINIT_MULTITHREADED` または `COINIT_APARTMENTTHREADED` と共に `CoInitializeEx` が呼び出されることを確認する必要があります。  
  
 エッジ モードでは、`debugApplication` パラメーターがサポートされていません。  エッジ モードでのこの API の使い方の詳細については、「[Edge エンジンとレガシ エンジンの比較](../chakra-hosting/targeting-edge-vs-legacy-engines-in-jsrt-apis.md)」を参照してください。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)