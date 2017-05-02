---
title: "for...in ステートメント (JavaScript) | Microsoft Docs"
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
  - "繰り返しステートメント, for...in ステートメント"
  - "ループ構造, for...in ステートメント"
ms.assetid: 1b51a0ce-89f7-4a69-88ed-017b47dc398f
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# for...in ステートメント (JavaScript)
オブジェクトの各プロパティ、または配列の各要素に対して、1 つ以上のステートメントを実行します。  
  
## 構文  
  
```  
for (variable in [object | array]) {  
    statements   
}  
```  
  
## パラメーター  
 `variable`  
 必須です。  `object` の任意のプロパティ名、または `array` の任意の要素インデックスを格納するために使用する変数を指定します。  
  
 `object`, `array`  
 省略可能です。  反復処理するオブジェクトまたは配列を指定します。  
  
 `statements`  
 省略可能です。  `object` のプロパティ、または `array` の各要素に対して実行する 1 つ以上のステートメントを指定します。  複合ステートメントを指定することもできます。  
  
## 解説  
 ループの各イテレーションを開始する前の `variable` の値は、`object` の次のプロパティ名、または `array` の次の要素インデックスです。  その後、ループ内の任意のステートメントで `variable` を使用して、`object` のプロパティまたは `array` の要素を参照できます。  
  
 オブジェクトのプロパティは、決まった方法では代入されません。  特定のプロパティを、そのインデックスで、プロパティの名前によってのみ指定することはできません。  
  
 配列の反復処理は、要素の順序、つまり、0、1、2 の順に実行されます。  
  
## 使用例  
 次のコードは、オブジェクトを連想配列として使用した `for...in` ステートメントの使用例です。  
  
```javascript  
// Initialize object.  
a = {"a" : "Athens" , "b" : "Belgrade", "c" : "Cairo"}  
  
// Iterate over the properties.  
var s = ""  
for (var key in a) {  
    s += key + ": " + a[key];  
    s += "<br />";  
    }  
document.write (s);  
  
// Output:  
// a: Athens  
// b: Belgrade  
// c: Cairo  
```  
  
## 使用例  
 expando プロパティを含む `Array` オブジェクトを反復処理する `for ... in` ステートメントを使用する例を次に示します。  
  
```javascript  
// Initialize the array.  
var arr = new Array("zero","one","two");  
  
// Add a few expando properties to the array.  
arr["orange"] = "fruit";  
arr["carrot"] = "vegetable";  
  
// Iterate over the properties and elements.  
var s = "";  
for (var key in arr) {  
    s += key + ": " + arr[key];  
    s += "<br />";  
}  
  
document.write (s);  
  
// Output:  
//   0: zero  
//   1: one  
//   2: two  
//   orange: fruit  
//   carrot: vegetable  
```  
  
> [!NOTE]
>  `Enumerator` オブジェクトを使用して、コレクションのメンバーを反復処理します。  
  
## 必要条件  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## 参照  
 [for ステートメント](../../javascript/reference/for-statement-javascript.md)   
 [while ステートメント](../../javascript/reference/while-statement-javascript.md)