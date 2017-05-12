---
title: "concat メソッド (Array) (JavaScript) | Microsoft Docs"
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
  - "concat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "concat メソッド (array)"
  - "Concat メソッド"
ms.assetid: bc2b4a6a-209e-4d59-8c24-59db01d53b1e
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# concat メソッド (Array) (JavaScript)
複数の配列を結合します。  
  
## 構文  
  
```  
  
array1.concat([item1[, item2[, . . . [, itemN]]]])   
```  
  
## パラメーター  
 `array1`  
 必須です。  他の配列が連結される `Array` オブジェクトを指定します。  
  
 `item1,. . ., itemN`  
 省略可能です。  `array1` の最後に追加する項目を指定します。  
  
## 解説  
 `concat` メソッドは、`array1` と他の項目を連結する配列が格納されている `Array` オブジェクトを返します。  
  
 配列に追加する項目 \(*item1 itemN*\) はリストの最初の項目から始めて、順番に追加されます。  いずれかの項目が配列の場合、配列のコンテンツが `array1` の末尾に追加されます。  項目が配列ではない場合、配列の末尾に 1 つの配列要素として追加されます。  
  
 元の配列の要素は、次のように結果の配列にコピーされます。  
  
-   連結前の配列から新しい配列にオブジェクトをコピーした場合、オブジェクト参照によって指定されるオブジェクトは変わりません。  新しい配列と元の配列のいずれかが変更されると、その変更は他方にも反映されます。  
  
-   新しい配列に数値型または文字列型の値が追加された場合は、値だけがコピーされます。  一方の配列の値を変更しても、他方の配列の値には影響しません。  
  
## 使用例  
 `concat` メソッドを配列に使用した例を次に示します。  
  
```javascript  
var a, b, c, d;  
a = new Array(1,2,3);  
b = "dog";  
c = new Array(42, "cat");  
d = a.concat(b, c);  
document.write(d);  
  
//Output:   
1, 2, 3, "dog", 42, "cat"  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 参照  
 [concat メソッド \(String\)](../../javascript/reference/concat-method-string-javascript.md)   
 [join メソッド \(Array\)](../../javascript/reference/join-method-array-javascript.md)