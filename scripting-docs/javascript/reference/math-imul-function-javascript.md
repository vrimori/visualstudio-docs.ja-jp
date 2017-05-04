---
title: "Math.imul 関数 (JavaScript) | Microsoft Docs"
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
ms.assetid: dce5e11c-36b9-4c39-84d3-6cd494dd1cbf
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Math.imul 関数 (JavaScript)
32 ビットの符号付き整数として扱われる 2 つの数値の積を返します。  
  
## 構文  
  
```  
Math.imul(x, y);  
```  
  
#### パラメーター  
 `x`  
 必須です。  最初の数値。  
  
 `y`  
 必須です。  2 番目の数値。  
  
## 解説  
 この関数は、JavaScript と同じ方法では整数の乗算を実装しない Emscripten や Mandreel などのコンパイラで使用されます。  
  
## 使用例  
 次のコード例では、`Math.imul` を使用して数値を乗算する方法を示しています。  
  
```javascript  
var result1 = Math.imul(2, 5);  
// result1 == 10  
  
var result2 = Math.imul(Math.pow(2, 32) - 1, Math.pow(2, 32) - 2);  
// result2 == 2  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]