---
title: "Array.of 関数 (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2884dda3-65d1-4990-9afe-87865c2d4f7f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Array.of 関数 (Array) (JavaScript)
引数として渡されたものから配列を返します。  
  
## 構文  
  
```  
Array.of(element0[, element1][, ...][,elementN]);  
```  
  
#### パラメーター  
 `element0,...,elementN`  
 省略可能です。  配列に代入する要素。  これにより、要素数が n \+ 1、長さが n \+ 1 の配列が作成されます。  
  
## 解説  
 この関数は `new Array(args)` の呼び出しに似ていますが、`Array.of` では 1 つの引数が渡されたときに、特別な処理は行われません。  
  
## 使用例  
 次の例では、渡された数値から配列を作成します。  
  
```javascript  
var arr = Array.of(1, 2, 3);  
// arr[0] == 1  
  
```  
  
## 使用例  
 次の例では、`Array.of` と `new Array` の使用方法の違いを示しています。  
  
```javascript  
var arr1 = Array.of(3);  
// arr1[0] == 3  
  
// With new Array, a single argument specifies  
// the length of the new array.  
var arr2 = new Array(3);  
// arr2[0] is undefined  
// arr2.length == 3  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]