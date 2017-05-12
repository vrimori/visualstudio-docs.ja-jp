---
title: "shift メソッド (Array) (JavaScript) | Microsoft Docs"
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
  - "shift"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "shift メソッド"
ms.assetid: f33baec5-f67e-4760-b7c1-553727bd0423
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# shift メソッド (Array) (JavaScript)
配列の先頭の要素を削除し、削除した要素を返します。  
  
## 構文  
  
```  
  
arrayObj.shift( )  
```  
  
#### パラメーター  
 The required `arrayObj` reference is an `Array` object.  
  
## 戻り値  
 配列から削除された要素を返します。  
  
## 解説  
 `shift` メソッドの使用例を次に示します。  
  
```javascript  
var arr = new Array(10, 11, 12);  
while (arr.length > 0)  
    {  
    var i = arr.shift();  
    document.write (i.toString() + " ");  
    }  
  
// Output:   
// 10 11 12  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 参照  
 [unshift メソッド \(Array\)](../../javascript/reference/unshift-method-array-javascript.md)