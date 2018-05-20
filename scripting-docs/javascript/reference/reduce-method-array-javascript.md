---
title: reduce メソッド (Array) (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- callback function, reduce method [JavaScript]
- arrays [JavaScript], reduce method
- reduce method [JavaScript]
ms.assetid: 48d069e0-e083-494f-86d5-d459d2377dc5
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d99f92d90885f26b19392b476ee64ae17bd40aed
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2018
---
# <a name="reduce-method-array-javascript"></a>reduce メソッド (Array) (JavaScript)
配列内のすべての要素には、指定されたコールバック関数を呼び出します。 コールバック関数の戻り値は収集された結果で、コールバック関数の次の呼び出しの引数として提供されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
array1.reduce(callbackfn[, initialValue])  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|定義|  
|---------------|----------------|  
|`array1`|必須。 配列オブジェクト。|  
|`callbackfn`|必須。 最大 4 つの引数を受け取る関数。 `reduce` メソッドは、配列内の各要素に対して `callbackfn` 関数を 1 回呼び出します。|  
|`initialValue`|任意。 場合`initialValue`を指定すると、蓄積を開始する初期値として使用されます。 最初の呼び出し、`callbackfn`関数は配列の値の代わりに、引数としてこの値を提供します。|  
  
## <a name="return-value"></a>戻り値  
 コールバック関数の最後の呼び出しから収集された結果です。  
  
## <a name="exceptions"></a>例外  
 A`TypeError`例外がスローされたときに、次の条件のいずれかが true:  
  
-   `callbackfn`引数が関数オブジェクトではありません。  
  
-   配列に要素が含まれていないと`initialValue`が指定されていません。  
  
## <a name="remarks"></a>コメント  
 場合、`initialValue`が指定されて、`reduce`メソッドの呼び出し、`callbackfn`関数をインデックスの昇順で、配列の各要素に対して 1 回です。 場合、`initialValue`が指定されていない、`reduce`メソッドの呼び出し、`callbackfn`以降 2 番目の要素で、各要素に対して関数。  
  
 コールバック関数の戻り値として提供される、`accumulator`コールバック関数に次の呼び出しで引数。 コールバック関数の最後の呼び出しの戻り値は、戻り値の`reduce`メソッドです。  
  
 配列内で欠落している要素に対しては、コールバック関数は呼び出されません。  
  
> [!NOTE]
>  [ReduceRight メソッド (Array)](../../javascript/reference/reduceright-method-array-javascript.md)降順のインデックスで要素を処理します。  
  
## <a name="callback-function-syntax"></a>コールバック関数の構文  
 コールバック関数の構文は次のとおりです。  
  
 `function callbackfn(accumulator, currentValue, currentIndex, array1)`  
  
 最大 4 つのパラメーターを使用して、コールバック関数を宣言することができます。  
  
 コールバック関数パラメーターの一覧を次の表に示します。  
  
|コールバック引数|定義|  
|-----------------------|----------------|  
|`accumulator`|コールバック関数には、前の呼び出しからの値。 場合、`initialValue`に提供される、 `reduce` 、メソッド、`accumulator`は`initialValue`初めて関数が呼び出されたとき。|  
|`currentValue`|現在の配列要素の値。|  
|`currentIndex`|現在の配列要素の数値インデックス。|  
|`array1`|要素を格納している配列オブジェクト。|  
  
## <a name="first-call-to-the-callback-function"></a>コールバック関数への最初の呼び出し  
 初めて、コールバック関数が呼び出されたとき、引数として渡された値依存かどうか、`reduce`メソッドには、`initialValue`引数。  
  
 場合、 `initialValue` reduce のメソッドに提供します。  
  
-   `accumulator` 引数が `initialValue` です。  
  
-   `currentValue`の引数は、最初の要素を配列内に存在します。  
  
 場合、`initialValue`が指定されていません。  
  
-   `accumulator`の引数は、最初の要素を配列内に存在します。  
  
-   `currentValue`の引数は、2 番目の要素を配列内に存在します。  
  
## <a name="modifying-the-array-object"></a>配列オブジェクトの変更  
 配列オブジェクトはコールバック関数で変更できます。  
  
 `reduce` メソッドの開始後に配列オブジェクトを変更した結果を次の表に示します。  
  
|`reduce` メソッドの開始後の条件|要素がコールバック関数に渡されるか?|  
|------------------------------------------------|------------------------------------------|  
|要素が配列の元の長さを越えて追加されている。|いいえ。|  
|要素はが、配列内の欠落した要素を補うために追加されている。|はい (そのインデックスがまだコールバック関数に渡されていない場合)。|  
|要素が変更されている。|はい (その要素がまだコールバック関数に渡されていない場合)。|  
|要素が配列から削除されている。|いいえ (その要素が既にコールバック関数に渡されている場合を除く)。|  
  
## <a name="example"></a>例  
 次の例では、配列の値を連結で値を分離する、文字列に"::"です。 初期値が提供されていないため、`reduce`としてメソッドをコールバック関数の最初の呼び出しでは"abc"、`accumulator`引数と"def"として、`currentValue`引数。  
  
```JavaScript  
// Define the callback function.  
function appendCurrent (accumulator, currentValue) {  
    return accumulator + "::" + currentValue;  
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
  
## <a name="example"></a>例  
 次の例は、丸められて後に、配列の値を追加します。 `reduce` 0 の初期値を持つメソッドが呼び出されます。  
  
```JavaScript  
// Define the callback function.  
function addRounded (accumulator, currentValue) {  
    return accumulator + Math.round(currentValue);  
    }  
  
// Create an array.  
var numbers = [10.9, 15.4, 0.5];  
  
// Call the reduce method, starting with an initial value of 0.  
var result = numbers.reduce(addRounded, 0);  
  
document.write (result);  
// Output: 27  
```  
  
## <a name="example"></a>例  
 次の例では、配列内の値を追加します。 `currentIndex`と`array1`パラメーター、コールバック関数で使用されます。  
  
```JavaScript  
function addDigitValue(accumulator, currentDigit, currentIndex, array) {  
    var exponent = (array.length - 1) - currentIndex;  
    var digitValue = currentDigit * Math.pow(10, exponent);  
    return accumulator + digitValue;  
    }  
  
var digits = [4, 1, 2, 5];  
  
// Determine an integer that is computed from values in the array.  
var result = digits.reduce(addDigitValue, 0);  
  
document.write (result);  
// Output: 4125  
```  
  
## <a name="example"></a>例  
 次の例は 1 ~ 10 を別の配列内の値のみを含む配列を取得します。 指定された初期値、`reduce`メソッドは空の配列。  
  
```JavaScript  
function Process(accumulatedArray, currentValue) {  
    // If currentValue is between 1 and 10,   
    // append currentValue to the array.  
    var nextArray;  
    if (currentValue >= 1 && currentValue <= 10)  
        nextArray = accumulatedArray.concat(currentValue);  
    else  
        nextArray = accumulatedArray;  
  
    // If this is not the last call by the reduce method,  
    // the returned array is accumulatedArray on the next call.  
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
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [reduceRight メソッド (Array)](../../javascript/reference/reduceright-method-array-javascript.md)
