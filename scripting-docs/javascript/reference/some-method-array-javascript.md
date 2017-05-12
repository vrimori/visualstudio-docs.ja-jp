---
title: "some メソッド (Array) (JavaScript) | Microsoft Docs"
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
  - "配列 [JavaScript], some メソッド"
  - "some メソッド [JavaScript]"
ms.assetid: 7b6822f9-c406-4f4e-bfec-a93459745992
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# some メソッド (Array) (JavaScript)
配列の任意の要素に対して、指定されたコールバック関数が `true` を返すかどうかを判定します。  
  
## 構文  
  
```  
  
array1.some(callbackfn[, thisArg])  
```  
  
#### パラメーター  
  
|パラメーター|定義|  
|------------|--------|  
|`array1`|必須です。  配列オブジェクト。|  
|`callbackfn`|必須です。  引数を 3 つまで受け取る関数。  `some` メソッドは、`array1` の各要素に対して、`callbackfn` が `true` を返すか、または配列の末尾に到達するまで `callbackfn` 関数を呼び出します。|  
|`thisArg`|省略可能です。  `this` のキーワードが `callbackfn` 関数内で参照できるオブジェクト。  `thisArg` を省略すると、`undefined` が `this` 値として使用されます。|  
  
## 戻り値  
 配列の任意の要素に対して `callbackfn` 関数が `true` を返す場合は `true`、それ以外の場合は `false` です。  
  
## 例外  
 `callbackfn` 引数が関数オブジェクトではない場合は、`TypeError` 例外がスローされます。  
  
## 解説  
 `some` メソッドは、`callbackfn` が `true` を返すまで、各要素に対してインデックスの昇順で `callbackfn` 関数を呼び出します。  `callbackfn` が `true` を返す原因になっている要素が見つかると、`some` メソッドは即座に `true` を返します。  コールバックがどの要素に対しても `true` を返さない場合、`some` メソッドは `false` を返します。  
  
 配列内で欠落している要素に対しては、コールバック関数は呼び出されません。  
  
 配列オブジェクトに加えて、`some` メソッドは `length` プロパティを持つオブジェクトおよび数値インデックス付きプロパティ名を持つオブジェクトで使用できます。  
  
> [!NOTE]
>  [every メソッド \(Array\)](../../javascript/reference/every-method-array-javascript.md) を使用すると、コールバック関数が配列のすべての要素に対して`true` を返すかどうかを確認できます。  
  
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
  
 `some` メソッドの開始後に配列オブジェクトを変更した結果を次の表に示します。  
  
|`some` メソッドの開始後の条件|要素がコールバック関数に渡されるか?|  
|------------------------|------------------------|  
|要素が配列の元の長さを越えて追加されている。|いいえ。|  
|要素はが、配列内の欠落した要素を補うために追加されている。|はい \(そのインデックスがまだコールバック関数に渡されていない場合\)。|  
|要素が変更されている。|はい \(その要素がまだコールバック関数に渡されていない場合\)。|  
|要素が配列から削除されている。|いいえ \(その要素が既にコールバック関数に渡されている場合を除く\)。|  
  
## 使用例  
 `some` メソッドを使用して、配列に偶数の要素があるかどうかを確認する例を次に示します。  
  
```javascript  
// The callback function.  
function CheckIfEven(value, index, ar) {  
    if (value % 2 == 0)  
        return true;  
}  
  
var numbers = [1, 15, 4, 10, 11, 22];  
  
var evens = numbers.some(CheckIfEven);  
document.write(evens);  
  
// Output:  
// true  
```  
  
## 使用例  
 `this` キーワードが参照できるオブジェクトを指定する `thisArg` パラメーターを使用する方法の例を次に示します。  これにより、渡されたオブジェクトによって指定される範囲外の数値が配列にあるかどうかを確認します。  
  
```javascript  
// Create a function that returns true if the value is   
// outside the range.  
var isOutsideRange = function (value) {  
    return value < this.minimum || value > this.maximum;  
}  
  
// Create an array of numbers.  
var numbers = [6, 12, 16, 22, -12];  
  
// The range object is to be the 'this' object.  
var range = { minimum: 10, maximum: 20 };  
  
document.write(numbers.some(isOutsideRange, range));  
  
// Output: true  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 参照  
 [every メソッド \(Array\)](../../javascript/reference/every-method-array-javascript.md)   
 [filter メソッド \(Array\)](../../javascript/reference/filter-method-array-javascript.md)   
 [map メソッド \(Array\)](../../javascript/reference/map-method-array-javascript.md)