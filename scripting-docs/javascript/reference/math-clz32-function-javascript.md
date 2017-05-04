---
title: "Math.clz32 関数 (JavaScript) | Microsoft Docs"
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
ms.assetid: 34615d7a-6d88-4ab5-a696-7e496caa51db
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Math.clz32 関数 (JavaScript)
32 ビットのバイナリ表記の数値における先行ゼロのビット数を返します。  
  
## 構文  
  
```  
  
Math.clz32(  
number  
)   
```  
  
## 解説  
 `number` が 0 の場合、結果は 32 になります。  `number` の 32 ビットのバイナリ エンコーディングの最上位ビットが 1 の場合、結果は 0 になります。  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **適用先**: [Math オブジェクト](../../javascript/reference/math-object-javascript.md)