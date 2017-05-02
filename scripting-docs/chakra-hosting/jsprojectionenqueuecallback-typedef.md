---
title: "JsProjectionEnqueueCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 19c1cefb-a7be-4196-b780-9fe6adf35ba5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# JsProjectionEnqueueCallback Typedef
元のスレッドと異なるスレッドで射影 API が完了したときに JsRT によって呼び出されるアプリケーションのコールバック。  
  
## 構文  
  
```  
typedef void (CALLBACK *JsProjectionEnqueueCallback)(  
  _In_ JsProjectionCallback jsCallback,  
  _In_ JsProjectionCallbackContext jsContext,  
  _In_opt_ void *callbackState  
);  
```  
  
#### パラメーター  
 `jsCallback`  
 元のスレッドで呼び出されるコールバック。  
  
 `jsContext`  
 アプリケーションのコンテキスト。  
  
 `callbackState`  
 `jsCallback` に渡す必要のある JsRT コンテキスト。  
  
## 解説  
 コールバックを受信するには、JsSetProjectionEnqueueCallback を呼び出す必要があります。  
  
 この API は、エッジ モードでのみサポートされます。  
  
## 必要条件  
 jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)