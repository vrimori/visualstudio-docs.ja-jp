---
title: "delete 演算子 (JavaScript) | Microsoft Docs"
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
  - "delete_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "配列要素、削除"
  - "プロパティ、削除"
  - "delete 演算子"
ms.assetid: 55c6487e-96ea-455b-a7ed-dc35c41ac2f3
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# delete 演算子 (JavaScript)
オブジェクトのプロパティ、または配列の要素を削除します。  
  
## 構文  
  
```  
delete expression  
```  
  
## 解説  
 `expression` 引数は、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] の有効な式です。通常はその結果がプロパティ名または配列要素になります。  
  
 `expression` の結果がオブジェクトで、`expression` で指定されたプロパティが存在し、さらにオブジェクトがそのプロパティの削除を禁止している場合は、`false` が返されます。  
  
 その他の場合は、`true` が返されます。  
  
## 使用例  
 配列から要素を削除する方法の例を次に示します。  
  
```javascript  
// Create an array.  
var ar = new Array (10, 11, 12, 13, 14);  
  
// Remove an element from the array.  
delete ar[1];  
  
// Print the results.  
document.write ("element 1: " + ar[1]);  
document.write ("<br />");  
document.write ("array: " + ar);  
// Output:  
//  element 1: undefined  
//  array: 10,,12,13,14  
```  
  
## 使用例  
 オブジェクトからプロパティを削除する方法の例を次に示します。  
  
```javascript  
// Create an object and add expando properties.  
var myObj = new Object();  
myObj.name = "Fred";  
myObj.count = 42;  
  
// Delete the properties from the object.  
delete myObj.name;  
delete myObj["count"];  
  
// Print the results.  
document.write ("name: " + myObj.name);  
document.write ("<br />");  
document.write ("count: " + myObj.count);  
// Output:  
//  name: undefined  
//  count: undefined  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 参照  
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)