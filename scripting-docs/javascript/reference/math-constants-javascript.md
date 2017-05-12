---
title: "数値演算定数 (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "LN2 定数 [JavaScript]"
  - "E 定数 [JavaScript]"
  - "LOG10E 定数 [JavaScript]"
  - "SQRT1_2 定数 [JavaScript]"
  - "LOG2E 定数 [JavaScript]"
  - "Math.SQRT2 定数 [JavaScript]"
  - "PI 定数 [JavaScript]"
  - "Math.LOG2E 定数 [JavaScript]"
  - "定数 [JavaScript]、数値演算"
  - "Math.E 定数 [JavaScript]"
  - "logarithm 定数 [JavaScript]"
  - "Math.LOG10E 定数 [JavaScript]"
  - "Math.SQRT1_2 定数 [JavaScript]"
  - "SQRT2 定数 [JavaScript]"
  - "平方根定数 [JavaScript]"
  - "Math.PI 定数 [JavaScript]"
  - "数値演算定数 [JavaScript]"
  - "LN10 定数 [JavaScript]"
  - "Math.LN2 定数 [JavaScript]"
  - "Math.LN10 定数 [JavaScript]"
ms.assetid: 8a674046-cb99-4103-92be-83697fba6344
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# 数値演算定数 (JavaScript)
数値演算定数は、`Math` オブジェクトのプロパティになっている定数値を返します。  
  
## Math オブジェクトの定数  
 [Math オブジェクト](../../javascript/reference/math-object-javascript.md)のプロパティになっている定数値を次の表に示します。  
  
|Constant|Description|概算値|  
|--------------|-----------------|---------|  
|`Math.E`|The mathematical constant e.  This is Euler's number, the base of natural logarithms.|2.718|  
|`Math.LN2`|The natural logarithm of 2.|0.693|  
|`Math.LN10`|The natural logarithm of 10.|2.302|  
|`Math.LOG2E`|The base\-2 logarithm of e.|1.443|  
|`Math.LOG10E`|The base\-10 logarithm of e.|0.434|  
|`Math.PI`|Pi.  This is the ratio of the circumference of a circle to its diameter.|3.14159|  
|`Math.SQRT1_2`|The square root of 0.5, or, equivalently, one divided by the square root of 2.|0.707|  
|`Math.SQRT2`|The square root of 2.|1.414|  
  
## 使用例  
 `Math.PI` 定数の使用方法を次の例に示します。  
  
```javascript  
var radius = 3;  
var area = Math.PI * radius * radius;  
document.write(area);  
  
// Output: 28.274333882308138  
  
```  
  
## 要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Applies To**: [Math オブジェクト](../../javascript/reference/math-object-javascript.md)  
  
## 参照  
 [Number 定数](../../javascript/reference/number-constants-javascript.md)   
 [JavaScript 定数](../../javascript/reference/javascript-constants.md)