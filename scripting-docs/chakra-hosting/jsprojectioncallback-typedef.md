---
title: "JsProjectionCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 32f22d37-e57e-4196-b6cd-a3fc75bd0632
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# JsProjectionCallback Typedef
正しいスレッドの `JsProjectionEnqueueCallback` に渡されたコンテキストによって呼び出される必要のある JsRT コールバック。  
  
## 構文  
  
```  
typedef void (CALLBACK *JsProjectionCallback)(  
  _In_ JsProjectionCallbackContext jsContext  
);  
```  
  
#### パラメーター  
 `jsContext`  
 コールバックを受信するには、`JsSetProjectionEnqueueCallback` を呼び出す必要があります。  
  
## 解説  
 この API は、エッジ モードでのみサポートされます。  
  
## 必要条件  
 jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)