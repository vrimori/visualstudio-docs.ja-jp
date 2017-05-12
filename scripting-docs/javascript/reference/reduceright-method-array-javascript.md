---
title: "reduceRight メソッド (Array) (JavaScript) | Microsoft Docs"
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
  - "配列 [JavaScript], reduceRight メソッド"
  - "reduceRight メソッド [JavaScript]"
ms.assetid: 85963761-da11-407c-8bce-278c930e61bd
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# reduceRight メソッド (Array) (JavaScript)
配列のすべての要素に対して、降順で指定されたコールバック関数を呼び出します。  コールバック関数の戻り値は累積結果であり、次のコールバック関数の呼び出しで引数として渡されます。  
  
## 構文  
  
```  
  
array1.reduceRight(callbackfn[, initialValue])  
```  
  
#### パラメーター  
  
|パラメーター|定義|  
|------------|--------|  
|`array1`|必須です。  配列オブジェクト。|  
|`callbackfn`|必須です。  引数を 4 つまで受け取る関数。  `reduceRight` メソッドは、配列内の各要素に対して `callbackfn` 関数を 1 回呼び出します。|  
|`initialValue`|省略可能です。  `initialValue` が指定されている場合は、積算を開始するための初期値として使用されます。  この値は、`callbackfn` 関数の最初の呼び出しによって、配列の値の代わりに引数として提供されます。|  
  
## 戻り値  
 最後のコールバック関数の呼び出しで収集された結果を含むオブジェクト。  
  
## 例外  
 次のどちらかの条件に当てはまる場合は、`TypeError` 例外がスローされます。  
  
-   `callbackfn` 引数が関数オブジェクトではない。  
  
-   配列に要素がなく、`initialValue` も提供されていない。  
  
## 解説  
 `initialValue` を指定すると、`reduceRight` メソッドは、配列の各要素に対して `callbackfn` 関数をインデックスの降順で 1 回呼び出します。  `initialValue` を指定しない場合、`reduceRight` メソッドは、各要素に対して `callbackfn` 関数を最後から 2 番目の要素から開始してインデックスの降順で呼び出します。  
  
 コールバック関数の戻り値は、コールバック関数の次の呼び出しに `previousValue` 引数として渡されます。  コールバック関数の最後の呼び出しの戻り値は、`reduceRight` メソッドの戻り値です。  
  
 配列内で欠落している要素に対しては、コールバック関数は呼び出されません。  
  
 インデックスの昇順で結果を収集するには、[reduce メソッド \(Array\)](../../javascript/reference/reduce-method-array-javascript.md) を使用します。  
  
## コールバック関数の構文  
 コールバック関数の構文は次のとおりです。  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 コールバック関数は、パラメーターを 4 つまで使用して宣言できます。  
  
 コールバック関数パラメーターの一覧を次の表に示します。  
  
|コールバックの引数|定義|  
|---------------|--------|  
|`previousValue`|前のコールバック関数呼び出しで得られた値。  `reduceRight` メソッドに `initialValue` が渡された場合は、関数が初めて呼び出されるときに `previousValue` が `initialValue` になります。|  
|`currentValue`|現在の配列の要素の値。|  
|`currentIndex`|現在の配列要素の数値インデックス。|  
|`array1`|要素を格納している配列オブジェクト。|  
  
## コールバック関数の最初の呼び出し  
 コールバック関数が初めて呼び出されるときに引数として渡される値は、`reduceRight` メソッドに `initialValue` 引数があるかどうかによって異なります。  
  
 `reduceRight` メソッドに `initialValue` が渡される場合:  
  
-   `previousValue` 引数は `initialValue` になります。  
  
-   `currentValue` 引数が配列内の最後の要素の値になります。  
  
 `initialValue` が指定されていない場合:  
  
-   `previousValue` 引数が配列内の最後の要素の値になります。  
  
-   `currentValue` 引数が配列内の最後から 2 番目の要素の値になります。  
  
## 配列オブジェクトの変更  
 配列オブジェクトはコールバック関数で変更できます。  
  
 `reduceRight` メソッドの開始後に配列オブジェクトを変更した結果を次の表に示します。  
  
|`reduceRight` メソッドの開始後の条件|要素がコールバック関数に渡されるか?|  
|-------------------------------|------------------------|  
|要素が配列の元の長さを越えて追加されている。|いいえ。|  
|要素はが、配列内の欠落した要素を補うために追加されている。|はい \(そのインデックスがまだコールバック関数に渡されていない場合\)。|  
|要素が変更されている。|はい \(その要素がまだコールバック関数に渡されていない場合\)。|  
|要素が配列から削除されている。|いいえ \(その要素が既にコールバック関数に渡されている場合を除く\)。|  
  
## 使用例  
 次の例では、配列の値を "::" で区切って文字列に連結します。  `reduceRight` メソッドに初期値が指定されていないので、コールバック関数への最初の呼び出しの `previousValue` 引数として 456、`currentValue` 引数として 123 が指定されます。  
  
```javascript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduceRight method, which calls the callback function  
// for each array element, in descending index order.  
var result = elements.reduceRight(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  456::123::def::abc  
```  
  
## 使用例  
 配列要素を 2 乗した値の合計を算出する例を次に示します。  `reduceRight` メソッドは初期値 0 で呼び出されます。  
  
```javascript  
// Define the callback function.  
function Process(previousValue, currentValue, index, array) {  
    // Add the previous value to the current value squared.  
    var nextValue = previousValue + (currentValue * currentValue);  
  
    // If this is not the last call by the reduceRight method,  
    // the return value is previousValue on the next call.  
    // If this is the last call by the reduceRight method, the  
    // return value is the return value of the reduceRight method.  
    return nextValue;  
}  
  
// Create an array.  
var numbers = [3, 4, 5];  
  
// Call the reduceRight method with an initial value of 0.  
var sumOfSquares = numbers.reduceRight(Process, 0);  
  
document.write("sum of squares=" + sumOfSquares);  
  
// Output:  
//  sum of squares=50  
```  
  
## 使用例  
 値が 1 ～ 10 の間にある配列内の要素を取得例を次に示します。  `reduceRight` メソッドの初期値は、空の配列です。  
  
```javascript  
function Process2(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduceRight method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduceRight method, the  
    // returned array is the return value of the reduceRight method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduceRight method, starting with an empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduceRight(Process2, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
//  result array=3,6,1  
```  
  
## 使用例  
 `reduceRight` メソッドは、文字列に適用できます。  このメソッドを使用して、文字列内の文字を逆転する方法の例を次に示します。  
  
```javascript  
// Define the callback function.  
function AppendToArray(previousValue, currentValue) {  
    return previousValue + currentValue;  
}  
  
var word = "retupmoc";  
  
// Create a string that reverses the characters of another string.  
// The commented-out statement shows an alternative syntax.  
var result = [].reduceRight.call(word, AppendToArray, "the ");  
// var result = Array.prototype.reduceRight.call(word, AppendToArray, "the ");  
  
document.write(result);  
  
// Output:  
// the computer  
```  
  
## 必要条件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 参照  
 [reduce メソッド \(Array\)](../../javascript/reference/reduce-method-array-javascript.md)