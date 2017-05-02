---
title: "forEach メソッド (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: 813bff6e-6098-4260-ab6e-b0d2da6be94d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# forEach メソッド (Set) (JavaScript)
セットの各要素に対して、指定された処理を実行します。  
  
## 構文  
  
```javascript  
setObj.forEach(callbackfn[, thisArg])  
```  
  
#### パラメーター  
 `setObj`  
 Required.  `Set` オブジェクト。  
  
 `callbackfn`  
 Required.  `callbackfn` は、最大で 3 つの引数を受け取ります。  `forEach` がセット内の各要素に対して 1 回呼び出す関数。  
  
 `thisArg`  
 Optional.  `this` キーワードが `callbackfn` 関数内で参照できるオブジェクト。  `thisArg` を省略すると、`undefined` が `this` 値として使用されます。  
  
## 例外  
 `callbackfn` 引数が関数オブジェクトではない場合は、`TypeError` 例外がスローされます。  
  
## 解説  
 コールバック関数の構文は次のとおりです。  
  
 `function callbackfn(value, key, setObj)`  
  
 コールバック関数は、次の表に示すパラメーターを最大 3 つ使用して宣言できます。  
  
|コールバック引数|定義|  
|--------------|--------|  
|`value`|セットに格納された値。|  
|`key`|セットに格納された値。  セットにキーがないため、この値は `value` と同じです。|  
|`setObj`|走査する `Set` オブジェクト。|  
  
## 使用例  
 次の例は、`forEach` を使用する方法を示しています。  `callbackfn` 引数には、コールバック関数のコードが含まれています。  
  
```javascript  
var s = new Set();  
  
s.add("scale");  
s.add(10);  
s.add("5");  
  
s.forEach(function(item, sameItem, s) {  
    document.write("Size of the set object is: " + s.size + "<br />");  
    document.write("Deleting item: " + item + "<br />");  
    s.delete(sameItem);  
});  
  
// Output:  
// Size of the set object is: 3  
// Deleting item: scale  
// Size of the set object is: 2  
// Deleting item: 10  
// Size of the set object is: 1  
// Deleting item: 5  
```  
  
## 使用例  
 次の例は、コールバック関数に 1 つのパラメーターのみを渡すことによってセットからメンバーを取得できることを示しています。  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]