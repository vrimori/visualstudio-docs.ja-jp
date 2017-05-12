---
title: "Math.min 関数 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "min"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "min メソッド"
ms.assetid: a1d7dd85-27ef-45cd-aa2a-f8e80f0b2898
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Math.min 関数 (JavaScript)
一連の数式の中で小さい数式を返します。  
  
## 構文  
  
```  
Math.min([number1[, number2[... [,numberN]]]])  
```  
  
## 解説  
 `number1, number2, ..., numberN` の省略可能な引数が評価される数値式です。  
  
 引数を指定しない場合の戻り値は、[Number.POSITIVE\_INFINITY](../../javascript/reference/number-constants-javascript.md) に等しくなります。  いずれかの引数が `NaN` の場合、戻り値も `NaN` になります。  
  
## 使用例  
 次のコードに、2 つの式の小さい方を取得する方法を示します。  
  
```javascript  
var x = Math.min(107 - 3, 48 * 90);  
document.write(x);  
  
// Output:  
// 104  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [Math.max 関数](../../javascript/reference/math-max-function-javascript.md)