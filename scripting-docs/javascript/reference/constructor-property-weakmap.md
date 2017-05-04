---
title: "constructor プロパティ (WeakMap) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1e3f9333-ce75-4d32-9b14-fbe81fd73dfb
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# constructor プロパティ (WeakMap)
`WeakMap` オブジェクトを作成する関数を指定します。  
  
## 構文  
  
```javascript  
weakmap.constructor  
```  
  
## 解説  
 `weakmap` 引数は必須で、`WeakMap` オブジェクトの名前を指定します。  
  
 `constructor` プロパティは、プロトタイプを持つあらゆるオブジェクトのプロトタイプのメンバーです。  これには、`Global` オブジェクトと `Math` オブジェクトを除くすべての組み込み JavaScript オブジェクトが含まれています。  `constructor` プロパティには、特定のオブジェクトのインスタンスを作成する関数への参照があります。  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]