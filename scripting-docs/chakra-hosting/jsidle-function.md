---
title: "JsIdle 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsIdle"
helpviewer_keywords: 
  - "JsIdle 関数"
ms.assetid: 372d1c62-8e19-4886-aa33-364cabc09bba
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# JsIdle 関数
必要なアイドル プロセスを行うようにランタイムに指示します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsIdle(  
   _Out_opt_ unsigned int *nextIdleTick  
);  
```  
  
#### パラメーター  
 `nextIdleTick`  
 さらにアイドル処理が存在する場合の次のシステム タイマー刻み。  null を使用できます。  以降のアイドル処理がない場合はタイマー刻みの最大数を返します。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 現在のランタイムでアイドル プロセスが有効である場合、呼び出し元の `JsIdle` はホストがアイドルであり、ランタイムがメモリ クリーンアップ タスクを実行できることを現在のランタイムに通知します。  
  
 `JsIdle` はまた、ランタイムにさらにアイドル作業が発生するまでのシステム タイマー刻みの数を返すことができます。  このタイマー刻みの数が経過する前に `JsIdle` を呼び出しても、処理は行われません。  
  
 アクティブ スクリプトのコンテキストが必要です。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)