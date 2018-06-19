---
title: forEach メソッド (Array) (JavaScript) |Microsoft ドキュメント
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
- forEach method [JavaScript]
- arrays [JavaScript], forEach method
- callback function, forEach method [JavaScript]
ms.assetid: bd188034-a62b-4cbd-99c8-46d70dd6823d
caps.latest.revision: 28
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec35c49e272ba50e26d3e4e7d892aa719a090d73
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637492"
---
# <a name="foreach-method-array-javascript"></a>forEach メソッド (Array) (JavaScript)
配列の各要素に対して、指定された処理を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
array1.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|定義|  
|---------------|----------------|  
|`array1`|必須です。 配列オブジェクト。|  
|`callbackfn`|必須です。 3 つまでの引数を受け取る関数。 `forEach` は、配列内の各要素に対して `callbackfn` 関数を 1 回呼び出します。|  
|`thisArg`|省略可能です。 `this` のキーワードが `callbackfn` 関数内で参照できるオブジェクト。 `thisArg` を省略すると、`undefined` が `this` 値として使用されます。|  
  
## <a name="exceptions"></a>例外  
 `callbackfn` 引数が関数オブジェクトではない場合は、`TypeError` 例外がスローされます。  
  
## <a name="remarks"></a>コメント  
 `forEach` メソッドは、配列内の各要素に対してインデックスの昇順に `callbackfn` 関数を 1 回呼び出します。 配列内で欠落している要素に対しては、コールバック関数は呼び出されません。  
  
 配列オブジェクトに加えて、`forEach` メソッドは、`length` プロパティを持つオブジェクトおよび数値インデックス付きプロパティ名を持つオブジェクトで使用できます。  
  
## <a name="callback-function-syntax"></a>コールバック関数の構文  
 コールバック関数の構文は次のとおりです。  
  
 `function callbackfn(value, index, array1)`  
  
 コールバック関数は、パラメーターを 3 つまで使用して宣言できます。  
  
 コールバック関数のパラメーターは次のとおりです。  
  
|コールバック引数|定義|  
|-----------------------|----------------|  
|`value`|配列の要素の値。|  
|`index`|配列要素の数値インデックス。|  
|`array1`|要素を格納している配列オブジェクト。|  
  
## <a name="modifying-the-array-object"></a>配列オブジェクトの変更  
 `forEach` メソッドが元の配列を直接変更することはありませんが、コールバック関数が変更することはあります。 `forEach` メソッドの開始後に配列オブジェクトを変更した結果を次の表に示します。  
  
|`forEach` メソッドの開始後の条件|要素がコールバック関数に渡されるか?|  
|---------------------------------------------|------------------------------------------|  
|要素が配列の元の長さを越えて追加されている。|いいえ。|  
|要素はが、配列内の欠落した要素を補うために追加されている。|はい (そのインデックスがまだコールバック関数に渡されていない場合)。|  
|要素が変更されている。|はい (その要素がまだコールバック関数に渡されていない場合)。|  
|要素が配列から削除されている。|いいえ (その要素が既にコールバック関数に渡されている場合を除く)。|  
  
## <a name="example"></a>例  
 `forEach` メソッドの使用例を次に示します。  
  
```JavaScript  
// Define the callback function.  
function ShowResults(value, index, ar) {  
    document.write("value: " + value);  
    document.write(" index: " + index);  
    document.write("<br />");  
}  
  
// Create an array.  
var letters = ['ab', 'cd', 'ef'];  
  
// Call the ShowResults callback function for each  
// array element.  
letters.forEach(ShowResults);  
  
// Output:  
//  value: ab index: 0   
//  value: cd index: 1   
//  value: ef index: 2   
```  
  
## <a name="example"></a>例  
 次の例では、コールバック関数のコードが `callbackfn` 引数に含まれています。  
  
```JavaScript  
// Create an array.  
var numbers = [10, 11, 12];  
  
// Call the addNumber callback function for each array element.  
var sum = 0;  
numbers.forEach(  
    function addNumber(value) { sum += value; }  
);  
  
document.write(sum);  
// Output: 33  
  
```  
  
## <a name="example"></a>例  
 `thisArg` キーワードを使用して参照できるオブジェクトを指定する `this` 引数の使用例を次に示します。  
  
```JavaScript  
// Define the object that contains the callback function.  
var obj = {  
    showResults: function(value, index) {  
        // Call calcSquare by using the this value.  
        var squared = this.calcSquare(value);  
  
        document.write("value: " + value);  
        document.write(" index: " + index);  
        document.write(" squared: " + squared);  
        document.write("<br />");  
    },  
    calcSquare: function(x) { return x * x }  
};  
  
// Define an array.  
var numbers = [5, 6];  
  
// Call the showResults callback function for each array element.  
// The obj is the this value within the   
// callback function.  
numbers.forEach(obj.showResults, obj);  
  
// Embed the callback function in the forEach statement.  
// The obj argument is the this value within the obj object.  
// The output is the same as for the previous statement.  
numbers.forEach(function(value, index) { this.showResults(value, index) }, obj);  
  
// Output:  
//  value: 5 index: 0 squared: 25  
//  value: 6 index: 1 squared: 36  
//  value: 5 index: 0 squared: 25  
//  value: 6 index: 1 squared: 36  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [filter メソッド (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [map メソッド (Array)](../../javascript/reference/map-method-array-javascript.md)   
 [some メソッド (Array)](../../javascript/reference/some-method-array-javascript.md)   
 [Array オブジェクト](../../javascript/reference/array-object-javascript.md)   
 [配列の使用](../../javascript/advanced/using-arrays-javascript.md)   
 [Hilo JavaScript のサンプル アプリ (Windows ストア)](http://hilojs.codeplex.com/SourceControl/latest)