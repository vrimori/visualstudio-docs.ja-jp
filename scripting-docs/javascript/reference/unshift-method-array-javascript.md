---
title: "unshift メソッド (Array) (JavaScript) | Microsoft Docs"
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
  - "unshift"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "unshift メソッド"
ms.assetid: 8c6a39ed-bab3-4ca4-9350-571a9427ec94
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# unshift メソッド (Array) (JavaScript)
配列の先頭に新しい要素を挿入します。  
  
## 構文  
  
```  
  
arrayObj.unshift([item1[, item2 [, . . . [, itemN]]]])  
```  
  
## パラメーター  
 `arrayObj`  
 必須です。  `Array` オブジェクト。  
  
 `item1, item2,. . ., itemN`  
 省略可能です。  `Array` の先頭に挿入する要素を指定します。  
  
## 解説  
 `unshift` メソッドでは、引数の並びと同じ順序で要素を配列の先頭に挿入します。  
  
## 使用例  
 `unshift` メソッドの使用例を次に示します。  
  
```javascript  
var ar = new Array();  
ar.unshift(10, 11);  
ar.unshift(12, 13, 14);  
document.write(ar.toString());  
  
// Output: 12,13,14,10,11  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 参照  
 [shift メソッド \(Array\)](../../javascript/reference/shift-method-array-javascript.md)