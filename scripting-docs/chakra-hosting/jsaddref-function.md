---
title: "JsAddRef 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsAddRef"
helpviewer_keywords: 
  - "JsAddRef 関数"
ms.assetid: a7f3ed49-6a86-489a-abdf-c99428e79cae
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsAddRef 関数
ガベージ コレクション オブジェクトへの参照を追加します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsAddRef(  
   _In_ JsRef ref,  
   _Out_opt_ unsigned int *count  
);  
```  
  
#### パラメーター  
 `ref`  
 参照を追加するオブジェクト。  
  
 `count`  
 オブジェクトの新しい参照カウント \(null 値を渡すことができます\)。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 これは、スタック上の場所に格納されない `JsRef` ハンドル上でのみ呼び出す必要があります。  `JsAddRef` を呼び出すことで、`JsRef` が呼び出されるまで、`JsRelease` が参照するオブジェクトが解放されないようにします。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)