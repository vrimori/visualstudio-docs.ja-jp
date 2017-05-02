---
title: "every メソッド (Array) (JavaScript) | Microsoft Docs"
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
  - "配列 [JavaScript], every メソッド"
  - "every メソッド"
ms.assetid: dc4ee2f8-fb9e-4c9f-af5a-fe836e40ddd1
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# every メソッド (Array) (JavaScript)
配列のすべてのメンバーが指定されているテストを満たすかどうかを判定します。  
  
## 構文  
  
```  
  
array1.every(callbackfn[, thisArg])  
```  
  
#### パラメーター  
  
|パラメーター|定義|  
|------------|--------|  
|`array1`|必須です。  配列オブジェクト。|  
|`callbackfn`|必須です。  引数を 3 つまで受け取る関数。  `every` メソッドは、`array1` の各要素に対して、`callbackfn` が `false` を返すか、または配列の末尾に到達するまで `callbackfn` 関数を呼び出します。|  
|`thisArg`|省略可能です。  `this` のキーワードが `callbackfn` 関数内で参照できるオブジェクト。  `thisArg` を省略すると、`undefined` が `this` 値として使用されます。|  
  
## 戻り値  
 配列のすべての要素に対して `callbackfn` 関数が `true` を返す場合は `true`、それ以外の場合は `false` です。  配列に要素がない場合、`every` メソッドは `true` を返します。  
  
## 例外  
 `callbackfn` 引数が関数オブジェクトではない場合は、`TypeError` 例外がスローされます。  
  
## 解説  
 `every` メソッドは、`callbackfn` 関数が `false` を返すまで、各配列要素に対してインデックスの昇順で `callbackfn` 関数を 1 回ずつ呼び出します。  `callbackfn` が `false` を返す原因になっている要素が見つかると、`every` メソッドは即座に `false` を返します。  それ以外の場合、`every` メソッドは `true` を返します。  
  
 配列内で欠落している要素に対しては、コールバック関数は呼び出されません。  
  
 配列オブジェクトに加えて、`every` メソッドは `length` プロパティを保有し、数値インデックス付きプロパティ名を保有する任意のオブジェクトに対して使用できます。  
  
> [!NOTE]
>  [some メソッド \(Array\)](../../javascript/reference/some-method-array-javascript.md) を使用すると、コールバック関数が配列のすべての要素に対して `true` を返すかどうかを確認できます。  
  
## コールバック関数の構文  
 コールバック関数の構文は次のとおりです。  
  
 `function callbackfn(value, index, array1)`  
  
 コールバック関数は、パラメーターを 3 つまで指定して宣言できます。  
  
 コールバック関数パラメーターの一覧を次の表に示します。  
  
|Callback パラメーター|定義|  
|---------------------|--------|  
|`value`|配列の要素の値。|  
|`index`|配列要素の数値インデックス。|  
|`array1`|要素を格納している配列オブジェクト。|  
  
## 配列オブジェクトの変更  
 配列オブジェクトはコールバック関数で変更できます。  
  
 `every` メソッドの開始後に配列オブジェクトを変更した結果を次の表に示します。  
  
|`every` メソッドの開始後の条件|要素がコールバック関数に渡されるか?|  
|-------------------------|------------------------|  
|要素が配列の元の長さを越えて追加されている。|いいえ。|  
|要素はが、配列内の欠落した要素を補うために追加されている。|はい \(そのインデックスがまだコールバック関数に渡されていない場合\)。|  
|要素が変更されている。|はい \(その要素がまだコールバック関数に渡されていない場合\)。|  
|要素が配列から削除されている。|いいえ \(その要素が既にコールバック関数に渡されている場合を除く\)。|  
  
## 使用例  
 `every` メソッドの使用例を次に示します。  
  
```javascript  
// Define the callback function.  
function CheckIfEven(value, index, ar) {  
    document.write(value + " ");  
  
    if (value % 2 == 0)  
        return true;  
    else  
        return false;  
}  
  
// Create an array.  
var numbers = [2, 4, 5, 6, 8];  
  
// Check whether the callback function returns true for all of the  
// array values.  
if (numbers.every(CheckIfEven))  
    document.write("All are even.");  
else  
    document.write("Some are not even.");  
  
// Output:  
// 2 4 5 Some are not even.  
```  
  
## 使用例  
 `this` キーワードで参照できるオブジェクトを指定する `thisArg` 引数の使用例を次に示します。  
  
```javascript  
// Create a function that returns true if the value is  
// numeric and within range.  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [10, 15, 19];  
  
// Check whether the callback function returns true for  
// all of the array values.  
// The obj argument enables use of the this value  
// within the callback function.  
  
var obj = { minimum: 10, maximum: 20 }  
  
if (numbers.every(checkNumericRange, obj))  
    document.write ("All are within range.");  
else  
    document.write ("Some are not within range.");  
  
// Output:  
//   All are within range.  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 参照  
 [some メソッド \(Array\)](../../javascript/reference/some-method-array-javascript.md)   
 [filter メソッド \(Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [Array オブジェクト](../../javascript/reference/array-object-javascript.md)   
 [配列の使用](../../javascript/advanced/using-arrays-javascript.md)