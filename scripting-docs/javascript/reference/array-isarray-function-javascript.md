---
title: "Array.isArray 関数 (JavaScript) | Microsoft Docs"
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
  - "Array.isArray 関数 [JavaScript]"
  - "isArray 関数 [JavaScript]"
ms.assetid: 58f7d2e0-d310-4292-b9bc-37a73c585780
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Array.isArray 関数 (JavaScript)
オブジェクトが配列であるかどうかを判別します。  
  
## 構文  
  
```  
Array.isArray(object)   
```  
  
#### パラメーター  
 `object`  
 必須です。  テストするオブジェクト。  
  
## 戻り値  
 `object` が配列である場合は `true`。それ以外の場合は `false`。  `object` 引数がオブジェクトではない場合、`false` が返されます。  
  
## 使用例  
 次の例は、`Array.isArray` 関数の使用方法を例示しています。  
  
```javascript  
var ar = [];  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = new Array();  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = [1, 2, 3];  
var result = Array.isArray(ar);  
// Output: true  
  
var result = Array.isArray("an array");  
document.write(result);  
// Output: false  
```  
  
## 必要条件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 参照  
 [Array オブジェクト](../../javascript/reference/array-object-javascript.md)   
 [配列の使用](../../javascript/advanced/using-arrays-javascript.md)   
 [typeof 演算子](../../javascript/reference/typeof-operator-decrementjavascript.md)