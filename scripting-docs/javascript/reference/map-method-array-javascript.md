---
title: "map メソッド (Array) (JavaScript) | Microsoft Docs"
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
  - "配列 [JavaScript], map メソッド"
  - "map メソッド [JavaScript]"
ms.assetid: 500dc4f8-d73d-4a28-a5b8-c9bd5674ea36
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# map メソッド (Array) (JavaScript)
定義されたコールバック関数を配列の各要素に対して呼び出し、結果を含む配列を返します。  
  
## 構文  
  
```  
  
array1.map(callbackfn[, thisArg])  
```  
  
#### パラメーター  
  
|パラメーター|定義|  
|------------|--------|  
|`array1`|必須。  配列オブジェクト。|  
|`callbackfn`|必須。  3 つまでの引数を受け取る関数。  `map` メソッドは、配列内の各要素に対して `callbackfn` 関数を 1 回呼び出します。|  
|`thisArg`|省略可能。  `this` のキーワードが `callbackfn` 関数内で参照できるオブジェクト。  `thisArg` を省略すると、`undefined` が `this` 値として使用されます。|  
  
## 戻り値  
 各要素が、対応する元の配列の要素に対するコールバック関数の戻り値である新しい配列。  
  
## 例外  
 `callbackfn` 引数が関数オブジェクトではない場合は、`TypeError` 例外がスローされます。  
  
## 解説  
 `map` メソッドは、配列の各要素に対してインデックスの昇順に `callbackfn` 関数を 1 回呼び出します。  配列内で欠落している要素に対しては、コールバック関数は呼び出されません。  
  
 配列オブジェクトに加えて、`map` メソッドは、`length` プロパティを持つオブジェクトおよび数値インデックス付きプロパティ名を持つオブジェクトで使用できます。  
  
## コールバック関数の構文  
 コールバック関数の構文は次のとおりです。  
  
 `function callbackfn(value, index, array1)`  
  
 コールバック関数は、パラメーターを 3 つまで使用して宣言できます。  
  
 コールバック関数パラメーターの一覧を次の表に示します。  
  
|コールバック引数|定義|  
|--------------|--------|  
|`value`|配列の要素の値。|  
|`index`|配列要素の数値インデックス。|  
|`array1`|要素を格納している配列オブジェクト。|  
  
## 配列オブジェクトの変更  
 配列オブジェクトはコールバック関数で変更できます。  
  
 `map` メソッドの開始後に配列オブジェクトを変更した結果を次の表に示します。  
  
|`map` メソッドの開始後の条件|要素がコールバック関数に渡されるか?|  
|-----------------------|------------------------|  
|要素が配列の元の長さを越えて追加されている。|いいえ。|  
|要素はが、配列内の欠落した要素を補うために追加されている。|はい \(そのインデックスがまだコールバック関数に渡されていない場合\)。|  
|要素が変更されている。|はい \(その要素がまだコールバック関数に渡されていない場合\)。|  
|要素が配列から削除されている。|いいえ \(その要素が既にコールバック関数に渡されている場合を除く\)。|  
  
## 使用例  
 `map` メソッドの使用例を次に示します。  
  
```javascript  
// Define the callback function.  
function AreaOfCircle(radius) {  
    var area = Math.PI * (radius * radius);  
    return area.toFixed(0);  
}  
  
// Create an array.  
var radii = [10, 20, 30];  
  
// Get the areas from the radii.  
var areas = radii.map(AreaOfCircle);  
  
document.write(areas);  
  
// Output:  
// 314,1257,2827  
```  
  
## 使用例  
 `this` キーワードで参照できるオブジェクトを指定する `thisArg` 引数の使用例を次に示します。  
  
```javascript  
// Define an object that contains a divisor property and  
// a remainder function.  
var obj = {  
    divisor: 10,  
    remainder: function (value) {  
        return value % this.divisor;  
    }  
}  
  
// Create an array.  
var numbers = [6, 12, 25, 30];  
  
// Get the remainders.  
// The obj argument specifies the this value in the callback function.  
var result = numbers.map(obj.remainder, obj);  
document.write(result);  
  
// Output:  
// 6,2,5,0  
```  
  
## 使用例  
 次の例では、組み込みの [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] メソッドがコールバック関数として使用されます。  
  
```javascript  
// Apply Math.sqrt(value) to each element in an array.  
var numbers = [9, 16];  
var result = numbers.map(Math.sqrt);  
  
document.write(result);  
// Output: 3,4  
```  
  
## 使用例  
 `map` メソッドは、文字列に適用できます。  次に例を示します。  
  
```javascript  
// Define the callback function.  
function threeChars(value, index, str) {  
    // Create a string that contains the previous, current,  
    // and next character.  
    return str.substring(index - 1, index + 2);  
}  
  
// Create a string.  
var word = "Thursday";  
  
// Apply the map method to the string.  
// Each array element in the result contains a string that  
// has the previous, current, and next character.  
// The commented out statement shows an alternative syntax.  
var result = [].map.call(word, threeChars);  
// var result = Array.prototype.map.call(word, threeChars);  
  
document.write(result);  
  
// Output:  
// Th,Thu,hur,urs,rsd,sda,day,ay  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 参照  
 [JavaScript メソッド](../../javascript/reference/javascript-methods.md)   
 [Array オブジェクト](../../javascript/reference/array-object-javascript.md)   
 [配列の使用](../../javascript/advanced/using-arrays-javascript.md)   
 [filter メソッド \(Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [forEach メソッド \(Array\)](../../javascript/reference/foreach-method-array-javascript.md)   
 [Hilo JavaScript のサンプル アプリ \(Windows ストア\)](http://hilojs.codeplex.com/SourceControl/latest)