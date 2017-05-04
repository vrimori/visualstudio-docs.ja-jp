---
title: "Math.round 関数 (JavaScript) | Microsoft Docs"
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
  - "round"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Math オブジェクト"
  - "Round メソッド"
ms.assetid: 51008df3-5d0c-4951-84cb-4f41000db0be
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Math.round 関数 (JavaScript)
指定された数式の値を整数に丸めて返します。  
  
## 構文  
  
```  
  
Math.round(  
number  
)   
```  
  
## 解説  
 必須の `number` 引数には、最も近い整数に丸める値を指定します。  
  
 正数では、`number` の小数部分が 0.5 以上の場合、`number` 以上の最小の整数が返されます。  小数部分が 0.5 未満の場合は、`number` 以下の最大の整数が返されます。  
  
 負数では、小数部分が 0.5 の場合、number より大きい最小の整数が返されます。  
  
 たとえば、`Math.round(8.5)` は 9 を返しますが、`Math.round(-8.5)` は \-8 を返します。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [Math オブジェクト](../../javascript/reference/math-object-javascript.md)  
  
## 参照  
 [Math.random 関数](../../javascript/reference/math-random-function-javascript.md)