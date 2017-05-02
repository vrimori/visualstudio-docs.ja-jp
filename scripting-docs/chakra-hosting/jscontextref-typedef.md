---
title: "JsContextRef Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 8586bfcc-bb24-430d-a6f2-1a3b3e34ec2e
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsContextRef Typedef
スクリプト コンテキストへの参照。  
  
## 構文  
  
```  
typedef JsRef JsContextRef;  
```  
  
## 解説  
 各スクリプト コンテキストには、他のスクリプト コンテキスト内のグローバル オブジェクトとは異なる独自のグローバル オブジェクトが含まれます。  
  
 多くの Chakra ホスト API では、`JsSetCurrentContext` を使用して設定できる "アクティブ" なスクリプト コンテキストが必要です。  現在のコンテキストの設定を必要とする Chakra ホスト API は、ドキュメントで明示的に示されます。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)