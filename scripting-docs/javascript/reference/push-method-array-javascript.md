---
title: "push メソッド (Array) (JavaScript) | Microsoft Docs"
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
  - "push"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Push メソッド"
ms.assetid: fa6e5799-dabe-4b3d-bd1f-0afc68c77134
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# push メソッド (Array) (JavaScript)
配列に新しい要素を追加し、その要素を追加した後の配列の長さを返します。  
  
## 構文  
  
```  
  
arrayObj.push([item1 [item2 [. . . [itemN ]]]])  
```  
  
## パラメーター  
 `arrayObj`  
 必須です。  `Array` オブジェクト。  
  
 `item, item2,. . ., itemN`  
 省略可能です。  `Array` の新しい要素を指定します。  
  
## 解説  
 `push` メソッドと `pop` メソッドでは後入れおよび先出しスタックをシミュレートすることができます。  
  
 `push` メソッドでは、引数に指定された順序で要素を追加します。  引数の 1 つが配列である場合は、1 つの要素として追加します。  複数の配列の要素を連結する場合は `concat` メソッドを使用します。  
  
## 使用例  
 `push` メソッドの使用例を次に示します。  
  
```javascript  
var number;  
var my_array = new Array();  
  
my_array.push (5, 6, 7);  
my_array.push (8, 9);  
  
number = my_array.pop();  
while (number != undefined)  
   {  
   document.write (number + " ");  
   number = my_array.pop();  
   }  
  
// Output:  
// 9 8 7 6 5  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 参照  
 [concat メソッド \(Array\)](../../javascript/reference/concat-method-array-javascript.md)   
 [pop メソッド \(Array\)](../../javascript/reference/pop-method-array-javascript.md)