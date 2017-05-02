---
title: "JsDisableRuntimeExecution 関数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsDisableRuntimeExecution"
helpviewer_keywords: 
  - "JsDisableRuntimeExecution 関数"
ms.assetid: 4bd4670a-a9da-4f8c-b3fd-1fd366d915c3
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# JsDisableRuntimeExecution 関数
スクリプトの実行を中断し、ランタイム内のすべての実行スクリプトを終了します。  
  
## 構文  
  
```  
STDAPI_(JsErrorCode) JsDisableRuntimeExecution(  
   _In_ JsRuntimeHandle runtime  
);  
```  
  
#### パラメーター  
 `runtime`  
 中断するランタイム。  
  
## 戻り値  
 操作が成功した場合はコード `JsNoError`、操作が失敗した場合はエラー コード。  
  
## 解説  
 中断されたランタイムの呼び出しは、`JsEnableRuntimeExecution` を呼び出すまで失敗します。  
  
 この API は、ランタイムがアクティブなスレッドで呼び出す必要はありません。  ランタイムは中断状態に設定されますが、スクリプトの実行は直ちに中断できません。実行中のスクリプトは、キャッチ不可能な例外により、できる限り早急に終了します。  
  
 既に中断されているランタイムで実行を中断しても何も行われません。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)