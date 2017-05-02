---
title: "splice メソッド (Array) (JavaScript) | Microsoft Docs"
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
  - "splice"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "splice メソッド"
ms.assetid: 85fdfb13-e3d9-4c89-b524-3ccee7001c93
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# splice メソッド (Array) (JavaScript)
配列から要素を削除し、必要に応じて新しい要素を削除位置に挿入します。その後、削除した要素を返します。  
  
## 構文  
  
```  
  
arrayObj.splice(start, deleteCount, [item1[, item2[, . . . [,itemN]]]])  
```  
  
## パラメーター  
 `arrayObj`  
 必須です。  `Array` オブジェクト。  
  
 `start`  
 必須です。  要素を削除する配列の削除開始位置を 0 から始まる番号で指定します。  
  
 `deleteCount`  
 必須です。  削除する要素の数を指定します。  
  
 `item1, item2,. . ., itemN`  
 省略可能です。  削除した要素の代わりに挿入する要素を指定します。  
  
## 解説  
 `splice` メソッドは、指定された数の要素を `start` の位置から削除し、新しい要素を挿入して `arrayObj` を修正します。  削除した要素は、新しい `Array` オブジェクトとして返されます。  
  
## 使用例  
 `splice` メソッドの使用例を次のコードに示します。  
  
```javascript  
var arr = new Array("4", "11", "2", "10", "3", "1");  
arr.splice(2, 2, "21", "31");  
document.write(arr);  
  
// Output: 4,11,21,31,3,1  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 参照  
 [slice メソッド \(Array\)](../../javascript/reference/slice-method-array-javascript.md)