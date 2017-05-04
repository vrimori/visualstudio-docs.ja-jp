---
title: "Math.max 関数 (JavaScript) | Microsoft Docs"
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
  - "max"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "max メソッド"
ms.assetid: f3ea1b8a-5fd0-482a-971b-b7f8e2b9b7eb
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Math.max 関数 (JavaScript)
指定された数式の中で大きい方の数式を返します。  
  
## 構文  
  
```  
Math.max([number1[, number2[... [, numberN]]]])   
```  
  
## 解説  
 `number1, number2, ..., numberN` の省略可能な引数が評価される数値式です。  
  
 引数を指定しない場合の戻り値は、[Number.NEGATIVE\_INFINITY](../../javascript/reference/number-constants-javascript.md) に等しくなります。  いずれかの引数が `NaN` の場合、戻り値も `NaN` になります。  
  
## 使用例  
 次のコードに、2 つの式の大きい方を取得する方法の例を次のコードに示します。  
  
```javascript  
var x = Math.max(107 - 3,  48 * 90);  
document.write(x);  
  
// Output:  
// 4320  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [Math.min 関数](../../javascript/reference/math-min-function-javascript.md)