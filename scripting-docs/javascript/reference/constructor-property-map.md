---
title: "constructor プロパティ (Map) | Microsoft Docs"
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
ms.assetid: a90d6a29-bd64-4e01-8d2f-988b7e3e4a24
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# constructor プロパティ (Map)
マップを作成する関数を指定します。  
  
## 構文  
  
```javascript  
map.constructor  
```  
  
## 解説  
 `map` はマップの名前で、必須です。  
  
 `constructor` プロパティは、プロトタイプを持つあらゆるオブジェクトのプロトタイプのメンバーです。  これには、`Global` オブジェクトと `Math` オブジェクトを除くすべての組み込み JavaScript オブジェクトが含まれています。  `constructor` プロパティには、特定のオブジェクトのインスタンスを作成する関数への参照があります。  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]