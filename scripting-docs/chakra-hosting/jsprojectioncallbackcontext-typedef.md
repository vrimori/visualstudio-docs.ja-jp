---
title: "JsProjectionCallbackContext Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 50c705c5-664f-4a1a-92f6-4882fc718ab1
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# JsProjectionCallbackContext Typedef
正しいスレッドのアプリケーションによって JsRT からアプリケーション コールバックの JsProjectionEnqueueCallback に渡され、指定されたコールバックの `JsProjectionCallback` の JsRT に返されたコンテキストです。  
  
## 構文  
  
```cpp  
typedef void *JsProjectionCallbackContext;  
```  
  
## 解説  
 コールバックを受信するには、`JsSetProjectionEnqueueCallback` を呼び出す必要があります。  
  
 この API は、エッジ モードでのみサポートされます。  
  
## 必要条件  
 jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)