---
title: "JsPromiseContinuationCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 51a3fd02-9668-4cf7-bb0b-e1fd03b2528f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsPromiseContinuationCallback Typedef
Promise 継続コールバック。  
  
## 構文  
  
```  
typedef void (CALLBACK *JsPromiseContinuationCallback)(  
  _In_ JsValueRef task,  
  _In_opt_ void *callbackState  
);  
```  
  
#### パラメーター  
 `task`  
  `callbackState`  
  
## 解説  
 ホストは、`JsSetPromiseContinuationCallback` の Promise 継続コールバックを指定できます。 スクリプトによって後で実行するタスクが作成される場合、Promise 継続コールバックがタスクと共に呼び出されます。現在のスクリプトの実行が完了したときにそのタスクが実行されるようにするには、タスクを FIFO キューに配置する必要があります。  
  
 この API は、エッジ モードでのみサポートされます。  
  
## 必要条件  
 jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)