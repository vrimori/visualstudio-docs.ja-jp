---
title: "forEach メソッド (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 9cdf0adc-77c7-4407-8ba7-ada0fb09e507
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# forEach メソッド (Map) (JavaScript)
マップの各要素に対して、指定された処理を実行します。  
  
## 構文  
  
```javascript  
mapObj.forEach(callbackfn[, thisArg])  
```  
  
#### パラメーター  
 `mapObj`  
 Required.  `Map` オブジェクト。  
  
 `callbackfn`  
 Required.  `forEach` がマップ内の各要素に対して 1 回呼び出す関数。  `callbackfn` は、最大で 3 つの引数を受け取ります。  `forEach` は、マップ内の各要素に対して `callbackfn` 関数を 1 回呼び出します。  
  
 `thisArg`  
 省略可能。  `this` キーワードが `callbackfn` 関数内で参照できるオブジェクト。  `thisArg` を省略すると、`undefined` が `this` 値として使用されます。  
  
## 例外  
 `callbackfn` 引数が関数オブジェクトではない場合は、`TypeError` 例外がスローされます。  
  
## 解説  
 コールバック関数の構文は次のとおりです。  
  
 `function callbackfn(value, key, mapObj)`  
  
 コールバック関数は、次の表に示すパラメーターを最大 3 つ使用して宣言できます。  
  
|コールバック引数|定義|  
|--------------|--------|  
|`value`|マップに格納された値。|  
|`key`|マップに格納されたキー。|  
|`mapObj`|走査する `Map` オブジェクト。|  
  
## 使用例  
 次の例は、`forEach` を使用して `Map` のメンバーを取得する方法を示します。  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]