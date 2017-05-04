---
title: "Math.hypot 関数 (JavaScript) | Microsoft Docs"
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
ms.assetid: 31488f5a-2230-4114-911e-b6d854c7b0a0
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Math.hypot 関数 (JavaScript)
引数の二乗の和の平方根を返します。  
  
## 構文  
  
```  
Math.hypot ( value1[, value2[, ...values] );  
```  
  
#### パラメーター  
 `value1`  
 必須です。  最初の数値。  
  
 `value2`  
 省略可能です。  2 番目の数値。  
  
 `values`  
 省略可能です。  1 つ以上の数値。  
  
## 解説  
 いずれかの引数が NaN の場合、関数は NaN を返します。  引数を指定しない場合、関数は 0 を返します。  
  
## 使用例  
 次の例では、`Math.hypot` 関数の使用例を示します。  
  
```javascript  
Math.hypot(3, 4);  
// Returns 5  
  
Math.hypot(3, "4");  
// Returns 5  
  
Math.hypot(3, "four");  
// Returns NaN   
  
Math.hypot(3, 4, 10);  
// Returns 11.180339887498949  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]