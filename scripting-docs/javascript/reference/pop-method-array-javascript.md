---
title: "pop メソッド (Array) (JavaScript) | Microsoft Docs"
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
  - "pop"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Pop メソッド"
ms.assetid: 4fae7f98-29f1-4041-ba43-601f2e5145ec
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# pop メソッド (Array) (JavaScript)
配列の最後の要素を削除し、削除した要素を返します。  
  
## 構文  
  
```  
  
arrayObj.pop( )  
```  
  
## 解説  
 [push](../../javascript/reference/push-method-array-javascript.md) メソッドと `pop` メソッドを使用すると、後入れ先出し \(LIFO: Last In First Out\) の原則に従ってデータを格納するスタックをシミュレートできます。  
  
 `arrayObj` 参照は必須で、`Array` オブジェクトを指定します。  
  
 配列が空の場合は、`undefined` を返します。  
  
## 使用例  
 `pop` メソッドの使用例を次に示します。  
  
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
  
// Output: 9 8 7 6 5  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 参照  
 [push メソッド \(Array\)](../../javascript/reference/push-method-array-javascript.md)