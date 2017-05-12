---
title: "JsBackgroundWorkItemCallback Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: e6db52e1-830c-46a2-b9f9-cc2d450a1da8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsBackgroundWorkItemCallback Typedef
バックグラウンド作業項目のコールバック。  
  
## 構文  
  
```  
typedef void (CALLBACK *JsBackgroundWorkItemCallback)(  
   _In_opt_ void *callbackData  
);  
```  
  
#### パラメーター  
 callbackData  
 スレッド サービスに渡されるデータ引数。  
  
## 解説  
 これは、ホストのスレッド サービスに渡されるので \(提供されている場合\)、ホストが選択したバックグラウンド スレッド上で作業項目コールバックを呼び出すことができます。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)