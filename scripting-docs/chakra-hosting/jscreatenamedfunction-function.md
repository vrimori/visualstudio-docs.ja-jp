---
title: "JsCreateNamedFunction 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 72f40d06-ab82-4fed-a632-68af6b4126c2
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsCreateNamedFunction 関数
名前付きの新しい JavaScript 関数を作成します。  
  
## 構文  
  
```cpp  
STDAPI_(JsErrorCode) JsCreateNamedFunction(  
   _In_ JsValueRef name,  
   _In_ JsNativeFunction nativeFunction,  
   _In_opt_ void *callbackState,  
   _Out_ JsValueRef *function  
);  
```  
  
#### パラメーター  
 `name`  
 診断目的および文字列化目的で使用されるこの関数の名前。  
  
 `nativeFunction`  
 関数が起動されたときに呼び出すメソッド。  
  
 `callbackState`  
 コールバックに返されるユーザー指定の状態。  
  
 `function`  
 新しい関数オブジェクト。  
  
## 戻り値  
  
## 解説  
 アクティブ スクリプトのコンテキストが必要です。  
  
 この API は、エッジ モードでのみサポートされます。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)