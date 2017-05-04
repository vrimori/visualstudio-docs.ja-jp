---
title: "reduce メソッド (Array) (JavaScript) | Microsoft Docs"
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
  - "配列 [JavaScript], reduce メソッド"
  - "callback 関数, reduce メソッド [JavaScript]"
  - "reduce メソッド [JavaScript]"
ms.assetid: 48d069e0-e083-494f-86d5-d459d2377dc5
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# reduce メソッド (Array) (JavaScript)
配列のすべての要素に対して、指定されたコールバック関数を呼び出します。  コールバック関数の戻り値は累積結果であり、次のコールバック関数の呼び出しで引数として渡されます。  
  
## 構文  
  
```  
  
array1.reduce(callbackfn[, initialValue])  
```  
  
#### パラメーター  
  
|パラメーター|定義|  
|------------|--------|  
|`array1`|必須です。  配列オブジェクト。|  
|`callbackfn`|必須です。  引数を 4 つまで受け取る関数。  `reduce` メソッドは、配列内の各要素に対して `callbackfn` 関数を 1 回呼び出します。|  
|`initialValue`|省略可能です。  `initialValue` が指定されている場合は、積算を開始するための初期値として使用されます。  この値は、`callbackfn` 関数の最初の呼び出しによって、配列の値の代わりに引数として提供されます。|  
  
## 戻り値  
 コールバック関数の最後の呼び出しで得られた累積結果。  
  
## 例外  
 次のどちらかの条件に当てはまる場合は、`TypeError` 例外がスローされます。  
  
-   `callbackfn` 引数が関数オブジェクトではない。  
  
-   配列に要素がなく、`initialValue` も提供されていない。  
  
## 解説  
 `initialValue` を指定すると、`reduce` メソッドは、配列に存在する各要素に対してインデックスの昇順に `callbackfn` 関数を 1 回呼び出します。  `initialValue` を指定しない場合、`reduce` メソッドは、2 番目の要素以降の各要素に対して、`callbackfn` 関数を呼び出します。  
  
 コールバック関数の戻り値は、コールバック関数の次の呼び出しに `previousValue` 引数として渡されます。  コールバック関数の最後の呼び出しの戻り値は、`reduce` メソッドの戻り値です。  
  
 配列内で欠落している要素に対しては、コールバック関数は呼び出されません。  
  
> [!NOTE]
>  [reduceRight メソッド \(Array\)](../../javascript/reference/reduceright-method-array-javascript.md) は要素をインデックスの降順に処理します。  
  
## コールバック関数の構文  
 コールバック関数の構文は次のとおりです。  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 コールバック関数は、パラメーターを 4 つまで使用して宣言できます。  
  
 コールバック関数パラメーターの一覧を次の表に示します。  
  
|コールバックの引数|定義|  
|---------------|--------|  
|`previousValue`|前のコールバック関数呼び出しで得られた値。  `reduce` メソッドに `initialValue` が渡された場合は、関数が初めて呼び出されるときに `previousValue` が `initialValue` になります。|  
|`currentValue`|現在の配列の要素の値。|  
|`currentIndex`|現在の配列要素の数値インデックス。|  
|`array1`|要素を格納している配列オブジェクト。|  
  
## コールバック関数の最初の呼び出し  
 コールバック関数が初めて呼び出されるときに引数として渡される値は、`reduce` メソッドに `initialValue` 引数があるかどうかによって異なります。  
  
 reduce メソッドに `initialValue` が渡される場合:  
  
-   `previousValue` 引数は `initialValue` になります。  
  
-   `currentValue` 引数は、配列内の最初の要素の値になります。  
  
 `initialValue` が指定されていない場合:  
  
-   `previousValue` 引数は、配列内の最初の要素の値になります。  
  
-   `currentValue` 引数は、配列内の 2 番目の要素の値になります。  
  
## 配列オブジェクトの変更  
 配列オブジェクトはコールバック関数で変更できます。  
  
 `reduce` メソッドの開始後に配列オブジェクトを変更した結果を次の表に示します。  
  
|`reduce` メソッドの開始後の条件|要素がコールバック関数に渡されるか?|  
|--------------------------|------------------------|  
|要素が配列の元の長さを越えて追加されている。|いいえ。|  
|要素はが、配列内の欠落した要素を補うために追加されている。|はい \(そのインデックスがまだコールバック関数に渡されていない場合\)。|  
|要素が変更されている。|はい \(その要素がまだコールバック関数に渡されていない場合\)。|  
|要素が配列から削除されている。|いいえ \(その要素が既にコールバック関数に渡されている場合を除く\)。|  
  
## 使用例  
 次の例では、配列の値を "::" で区切って文字列に連結します。  `reduce` メソッドに初期値が指定されていないので、コールバック関数の最初の呼び出しでは、`previousValue` 引数として abc、`currentValue` 引数として def が指定されます。  
  
```javascript  
// Define the callback function.  
function appendCurrent (previousValue, currentValue) {  
    return previousValue + "::" + currentValue;  
    }  
  
// Create an array.  
var elements = ["abc", "def", 123, 456];  
  
// Call the reduce method, which calls the callback function  
// for each array element.  
var result = elements.reduce(appendCurrent);  
  
document.write(result);  
  
// Output:  
//  abc::def::123::456  
  
```  
  
## 使用例  
 次の例では、配列の値を丸めてから加算します。  `reduce` メソッドは初期値 0 で呼び出されます。  
  
```javascript  
// Define the callback function.  
function addRounded (previousValue, currentValue) {  
    return previousValue + Math.round(currentValue);  
    }  
  
// Create an array.  
var numbers = [10.9, 15.4, 0.5];  
  
// Call the reduce method, starting with an initial value of 0.  
var result = numbers.reduce(addRounded, 0);  
  
document.write (result);  
// Output: 27  
```  
  
## 使用例  
 次の例では、配列の値を追加します。  コールバック関数では、`currentIndex` パラメーターと `array1` パラメーターが使用されます。  
  
```javascript  
function addDigitValue(previousValue, currentDigit, currentIndex, array) {  
    var exponent = (array.length - 1) - currentIndex;  
    var digitValue = currentDigit * Math.pow(10, exponent);  
    return previousValue + digitValue;  
    }  
  
var digits = [4, 1, 2, 5];  
  
// Determine an integer that is computed from values in the array.  
var result = digits.reduce(addDigitValue, 0);  
  
document.write (result);  
// Output: 4125  
```  
  
## 使用例  
 次の例では、別の配列の 1 ～ 10 の値のみを含む配列を取得します。  `reduce` メソッドの初期値は、空の配列です。  
  
```javascript  
function Process(previousArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = previousArray.concat(currentValue);  
    else  
        nextArray = previousArray;  
  
    // If this is not the last call by the reduce method,  
    // the returned array is previousArray on the next call.  
    // If this is the last call by the reduce method, the  
    // returned array is the return value of the reduce method.  
    return nextArray;  
}  
  
// Create an array.  
var numbers = [20, 1, -5, 6, 50, 3];  
  
// Call the reduce method, starting with an initial empty array.  
var emptyArray = new Array();  
var resultArray = numbers.reduce(Process, emptyArray);  
  
document.write("result array=" + resultArray);  
  
// Output:  
// result array=1,6,3  
```  
  
## 必要条件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 参照  
 [reduceRight メソッド \(Array\)](../../javascript/reference/reduceright-method-array-javascript.md)