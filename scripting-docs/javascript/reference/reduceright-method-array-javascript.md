---
title: reduceRight メソッド (Array) (JavaScript) |Microsoft ドキュメント
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
- arrays [JavaScript], reduceRight method
- reduceRight method [JavaScript]
ms.assetid: 85963761-da11-407c-8bce-278c930e61bd
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d7fd2794157eadacefa7404f9333c51aed9425c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641922"
---
# <a name="reduceright-method-array-javascript"></a>reduceRight メソッド (Array) (JavaScript)
降順で、配列内のすべての要素には、指定されたコールバック関数を呼び出します。 コールバック関数の戻り値は収集された結果で、コールバック関数の次の呼び出しの引数として提供されます。  
  
## <a name="syntax"></a>構文  
  
```  
  
array1.reduceRight(callbackfn[, initialValue])  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|定義|  
|---------------|----------------|  
|`array1`|必須です。 配列オブジェクト。|  
|`callbackfn`|必須です。 最大 4 つの引数を受け取る関数。 `reduceRight` メソッドは、配列内の各要素に対して `callbackfn` 関数を 1 回呼び出します。|  
|`initialValue`|省略可能です。 場合`initialValue`を指定すると、蓄積を開始する初期値として使用されます。 最初の呼び出し、`callbackfn`関数は配列の値の代わりに、引数としてこの値を提供します。|  
  
## <a name="return-value"></a>戻り値  
 コールバック関数の最後の呼び出しから収集された結果を格納するオブジェクト。  
  
## <a name="exceptions"></a>例外  
 A`TypeError`例外がスローされたときに、次の条件のいずれかが true:  
  
-   `callbackfn`引数が関数オブジェクトではありません。  
  
-   配列に要素が含まれていないと`initialValue`が指定されていません。  
  
## <a name="remarks"></a>コメント  
 場合、`initialValue`が指定されて、`reduceRight`メソッドの呼び出し、`callbackfn`関数をインデックス順に並べられて、配列の各要素に対して 1 回です。 ない場合は`initialValue`が指定されて、`reduceRight`メソッドの呼び出し、`callbackfn`インデックスを降順で、最後から 2 番目の要素から始めて、各要素に対して関数。  
  
 コールバック関数の戻り値として提供される、`previousValue`コールバック関数に次の呼び出しで引数。 コールバック関数の最後の呼び出しの戻り値は、戻り値の`reduceRight`メソッドです。  
  
 配列内で欠落している要素に対しては、コールバック関数は呼び出されません。  
  
 インデックスの昇順で結果を蓄積するを使用して、 [reduce メソッド (Array)](../../javascript/reference/reduce-method-array-javascript.md)です。  
  
## <a name="callback-function-syntax"></a>コールバック関数の構文  
 コールバック関数の構文は次のとおりです。  
  
 `function callbackfn(previousValue, currentValue, currentIndex, array1)`  
  
 最大 4 つのパラメーターを使用して、コールバック関数を宣言することができます。  
  
 コールバック関数パラメーターの一覧を次の表に示します。  
  
|コールバック引数|定義|  
|-----------------------|----------------|  
|`previousValue`|コールバック関数には、前の呼び出しからの値。 場合、`initialValue`に提供される、 `reduceRight` 、メソッド、`previousValue`は`initialValue`初めて関数が呼び出されたとき。|  
|`currentValue`|現在の配列要素の値。|  
|`currentIndex`|現在の配列要素の数値インデックス。|  
|`array1`|要素を格納している配列オブジェクト。|  
  
## <a name="first-call-to-the-callback-function"></a>コールバック関数への最初の呼び出し  
 初めて、コールバック関数が呼び出されたとき、引数として渡された値依存かどうか、`reduceRight`メソッドには、`initialValue`引数。  
  
 場合、`initialValue`に提供される、`reduceRight`メソッド。  
  
-   `previousValue` 引数が `initialValue` です。  
  
-   `currentValue`の引数は、最後の要素を配列内に存在します。  
  
 場合、`initialValue`が指定されていません。  
  
-   `previousValue`の引数は、最後の要素を配列内に存在します。  
  
-   `currentValue`引数は、最後から 2 番目の要素の値、配列内に存在します。  
  
## <a name="modifying-the-array-object"></a>配列オブジェクトの変更  
 配列オブジェクトはコールバック関数で変更できます。  
  
 `reduceRight` メソッドの開始後に配列オブジェクトを変更した結果を次の表に示します。  
  
|`reduceRight` メソッドの開始後の条件|要素がコールバック関数に渡されるか?|  
|-----------------------------------------------------|------------------------------------------|  
|要素が配列の元の長さを越えて追加されている。|いいえ。|  
|要素はが、配列内の欠落した要素を補うために追加されている。|はい (そのインデックスがまだコールバック関数に渡されていない場合)。|  
|要素が変更されている。|はい (その要素がまだコールバック関数に渡されていない場合)。|  
|要素が配列から削除されている。|いいえ (その要素が既にコールバック関数に渡されている場合を除く)。|  
  
## <a name="example"></a>例  
 次の例では、配列の値を連結で値を分離する、文字列に"::"です。 初期値が提供されていないため、`reduceRight`メソッド、コールバック関数に最初の呼び出しでとして 456、`previousValue`引数と同様の 123、`currentValue`引数。  
  
```JavaScript  
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
  
## <a name="example"></a>例  
 次の例では、配列の要素の 2 乗の合計を検索します。 `reduceRight` 0 の初期値を持つメソッドが呼び出されます。  
  
```JavaScript  
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
  
## <a name="example"></a>例  
 次の例では、配列の値を持つの 1 ~ 10 のそれらの要素を取得します。 指定された初期値、`reduceRight`メソッドは空の配列。  
  
```JavaScript  
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
  
## <a name="example"></a>例  
 `reduceRight` メソッドは、文字列に適用できます。 次の例では、このメソッドを使用して、文字列内の文字を反転する方法を示します。  
  
```JavaScript  
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
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [reduce メソッド (Array)](../../javascript/reference/reduce-method-array-javascript.md)