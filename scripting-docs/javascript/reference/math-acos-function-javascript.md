---
title: "Math.acos 関数 (JavaScript) | Microsoft Docs"
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
  - "acos"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "acos メソッド"
  - "arcosine メソッド"
ms.assetid: 828cb3c3-bdf7-4bb7-97ae-3617ce4b2d62
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Math.acos 関数 (JavaScript)
数値のアーク コサイン \(または逆コサイン\) を返します。  
  
## 構文  
  
```  
Math.acos(number)  
```  
  
#### パラメーター  
 `number` 引数は必須で、数式を指定します。  
  
## 戻り値  
 `number` 引数のアーク コサイン \(ラジアン単位\)。  
  
## 使用例  
 `acos` 関数の使用方法を次のコード例に示します。  
  
```javascript  
var v1 = Math.acos(-1.0);  
var v2 = Math.cos(-1.0);  
  
document.write(v1);  
document.write("<br/>");  
document.write(v2);  
  
// Output:  
// 3.141592653589793  
// 0.5403023058681398  
  
```  
  
## 解説  
 **対象**: [Math オブジェクト](../../javascript/reference/math-object-javascript.md)  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [Math.asin 関数](../../javascript/reference/math-asin-function-javascript.md)   
 [Math.atan 関数](../../javascript/reference/math-atan-function-javascript.md)   
 [Math.cos 関数](../../javascript/reference/math-cos-function-javascript.md)   
 [Math.sin 関数](../../javascript/reference/math-sin-function-javascript.md)   
 [Math.tan 関数](../../javascript/reference/math-tan-function-javascript.md)   
 [Math オブジェクト](../../javascript/reference/math-object-javascript.md)