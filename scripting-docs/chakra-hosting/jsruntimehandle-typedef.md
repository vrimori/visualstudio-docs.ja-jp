---
title: "JsRuntimeHandle Typedef | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 69e59bfd-9b0e-4710-9aa8-fbd6844171bc
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# JsRuntimeHandle Typedef
Chakra ランタイムへのハンドル。  
  
## 構文  
  
```  
typedef void *JsRuntimeHandle;  
```  
  
## 解説  
 各 Chakra ランタイムには、独自の独立した実行エンジン、JIT コンパイラ、およびガベージ コレクション ヒープがあります。  このために、各ランタイムは他のランタイムから完全に分離されています。  
  
 ランタイムは、任意のスレッドで使用できますが、任意の時点で 1 つのスレッドのみがランタイムを呼び出すことができます。  
  
> [!WARNING]
>  JsRuntimeHandle は、Chakra ホスト API の他のオブジェクト参照とは異なり、ガベージ コレクション ヒープ自体を含むので、ガベージ コレクションは行われません。  ランタイムは、JsDisposeRuntime を呼び出すまで存続します。  
  
## 必要条件  
 **ヘッダー:** jsrt.h  
  
## 参照  
 [リファレンス \(JavaScript ランタイム\)](../chakra-hosting/reference-javascript-runtime.md)