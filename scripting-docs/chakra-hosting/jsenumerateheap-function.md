---
title: "JsEnumerateHeap 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsEnumerateHeap"
helpviewer_keywords: 
  - "JsEnumerateHeap 関数"
ms.assetid: 3e518e0b-b959-4686-899c-83e6b1946c9d
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsEnumerateHeap 関数
現在のコンテキストのヒープを列挙します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsEnumerateHeap(  
   _Out_ IActiveScriptProfilerHeapEnum **enumerator  
);  
```  
  
#### パラメーター  
 `enumerator`  
 ヒープの列挙子。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 ヒープの列挙中に現在のコンテキストは削除できません。また、ヒープ列挙子が解放されるまで、コンテキストの状態を変更するための呼び出しはすべて失敗します。  
  
 アクティブ スクリプトのコンテキストが必要です。  
  
 この API はデスクトップ アプリではサポートされますが、ストア アプリではサポートされません。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)