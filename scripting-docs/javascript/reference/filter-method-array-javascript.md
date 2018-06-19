---
title: filter メソッド (Array) (JavaScript) |Microsoft ドキュメント
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
- arrays [JavaScript], filter method
- filter method [JavaScript]
ms.assetid: 1d260370-9e6e-43fc-870f-2d35850db7ee
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33a08fdba38de558dabc749a634fb9b69c52c98a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637782"
---
# <a name="filter-method-array-javascript"></a>filter メソッド (Array) (JavaScript)
コールバック関数で指定された条件を満たす、配列の要素を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
array1.filter(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|定義|  
|---------------|----------------|  
|`array1`|必須です。 配列オブジェクト。|  
|`callbackfn`|必須です。 3 つまでの引数を受け取る関数。 `filter` メソッドは、配列内の各要素に対して `callbackfn` 関数を 1 回呼び出します。|  
|`thisArg`|省略可能です。 `this` のキーワードが `callbackfn` 関数内で参照できるオブジェクト。 `thisArg` を省略すると、`undefined` が `this` 値として使用されます。|  
  
## <a name="return-value"></a>戻り値  
 コールバック関数を返す対象のすべての値を格納する新しい配列`true`です。 コールバック関数を返した場合`false`のすべての要素の`array1`、新しい配列の長さが 0 です。  
  
## <a name="exceptions"></a>例外  
 `callbackfn` 引数が関数オブジェクトではない場合は、`TypeError` 例外がスローされます。  
  
## <a name="remarks"></a>コメント  
 `filter` メソッドは、配列の各要素に対してインデックスの昇順に `callbackfn` 関数を 1 回呼び出します。 配列内で欠落している要素に対しては、コールバック関数は呼び出されません。  
  
 配列オブジェクトに加えて、`filter` メソッドは、`length` プロパティを持つオブジェクトおよび数値インデックス付きプロパティ名を持つオブジェクトで使用できます。  
  
## <a name="callback-function-syntax"></a>コールバック関数の構文  
 コールバック関数の構文は次のとおりです。  
  
 `function callbackfn(value, index, array1)`  
  
 コールバック関数は、パラメーターを 3 つまで使用して宣言できます。  
  
 コールバック関数パラメーターの一覧を次の表に示します。  
  
|コールバック引数|定義|  
|-----------------------|----------------|  
|`value`|配列の要素の値。|  
|`index`|配列要素の数値インデックス。|  
|`array1`|要素を格納している配列オブジェクト。|  
  
## <a name="modifying-the-array-object"></a>配列オブジェクトの変更  
 `filter` メソッドが元の配列を直接変更することはありませんが、コールバック関数が変更することはあります。 `filter` メソッドの開始後に配列オブジェクトを変更した結果を次の表に示します。  
  
|`filter` メソッドの開始後の条件|要素がコールバック関数に渡されるか?|  
|------------------------------------------------|------------------------------------------|  
|要素が配列の元の長さを越えて追加されている。|いいえ。|  
|要素はが、配列内の欠落した要素を補うために追加されている。|はい (そのインデックスがまだコールバック関数に渡されていない場合)。|  
|要素が変更されている。|はい (その要素がまだコールバック関数に渡されていない場合)。|  
|要素が配列から削除されている。|いいえ (その要素が既にコールバック関数に渡されている場合を除く)。|  
  
## <a name="example"></a>例  
 `filter` メソッドを使用する方法の例を次に示します。  
  
```JavaScript  
// Define a callback function.  
function CheckIfPrime(value, index, ar) {  
    high = Math.floor(Math.sqrt(value)) + 1;  
  
    for (var div = 2; div <= high; div++) {  
        if (value % div == 0) {  
            return false;  
        }  
    }   
    return true;  
}  
  
// Create the original array.  
var numbers = [31, 33, 35, 37, 39, 41, 43, 45, 47, 49, 51, 53];  
  
// Get the prime numbers that are in the original array.   
var primes = numbers.filter(CheckIfPrime);  
  
document.write(primes);  
// Output: 31,37,41,43,47,53  
```  
  
## <a name="example"></a>例  
 次の例では、コールバック関数のコードが `callbackfn` 引数に含まれています。  
  
```JavaScript  
// Create the original array.  
var arr = [5, "element", 10, "the", true];  
  
// Create an array that contains the string  
// values that are in the original array.  
var result = arr.filter(  
    function (value) {  
        return (typeof value === 'string');  
    }  
);  
  
document.write(result);  
// Output: element, the  
```  
  
## <a name="example"></a>例  
 次の例は、先頭に文字"css"プロパティの名前を表示、 `window` DOM オブジェクト。  
  
```JavaScript  
var filteredNames = Object.getOwnPropertyNames(window).filter(IsC);  
  
    for (i in filteredNames)  
        document.write(filteredNames[i] + "<br/>");  
  
// Check whether the string starts with "css".  
function IsC(value) {  
    var firstChar = value.substr(0, 3);  
    if (firstChar.toLowerCase() == "css")  
        return true;  
    else  
        return false;  
    }  
  
// Output:  
// CSSRule  
// CSSFontFaceRule  
// CSSImportRule  
// CSSMediaRule  
// CSSNamespaceRule  
// CSSPageRule  
// CSSRuleList  
// CSSStyleDeclaration  
// CSSStyleRule  
// CSSStyleSheet  
  
```  
  
## <a name="example"></a>例  
 `thisArg` キーワードで参照できるオブジェクトを指定する `this` 引数の使用例を次に示します。  
  
```JavaScript  
var checkNumericRange = function(value) {  
    if (typeof value !== 'number')  
        return false;  
    else   
        return value >= this.minimum && value <= this.maximum;  
}  
  
var numbers = [6, 12, "15", 16, "the", -12];  
  
// The obj argument enables use of the this value  
// within the callback function.  
var obj = { minimum: 10, maximum: 20 }  
  
var result = numbers.filter(checkNumericRange, obj);  
  
document.write(result);  
// Output: 12,16  
  
```  
  
## <a name="example"></a>例  
 `filter`メソッドは、配列の代わりに、文字列に適用できます。 その方法を次の例に示します。  
  
```JavaScript  
// Define a callback function that returns true  
// if the current array element follows a space  
// or is the first character.  
function CheckValue(value, index, ar) {  
    if (index == 0)  
        return true;  
    else  
        return ar[index - 1] === " ";  
}  
  
// Create a string.  
var sentence = "The quick brown fox jumps over the lazy dog.";   
  
// Create an array that contains all characters that follow a space.  
var subset = [].filter.call(sentence, CheckValue);   
  
// You can use this alternative syntax.  
//var subset = Array.prototype.filter.call(sentence, CheckValue);  
  
document.write(subset);  
// Output: T,q,b,f,j,o,t,l,d  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Array オブジェクト](../../javascript/reference/array-object-javascript.md)   
 [配列の使用](../../javascript/advanced/using-arrays-javascript.md)   
 [map メソッド (Array)](../../javascript/reference/map-method-array-javascript.md)   
 [forEach メソッド (Array)](../../javascript/reference/foreach-method-array-javascript.md)