---
title: "every メソッド (Array) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- every method
- arrays [JavaScript], every method
ms.assetid: dc4ee2f8-fb9e-4c9f-af5a-fe836e40ddd1
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a05263ae45df61c47a3580d474863c8d4ff3dd1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="every-method-array-javascript"></a>every メソッド (Array) (JavaScript)
配列のすべてのメンバーが、指定したテストを満たすかどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```  
  
array1.every(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|定義|  
|---------------|----------------|  
|`array1`|必須です。 配列オブジェクト。|  
|`callbackfn`|必須です。 3 つまでの引数を受け取る関数。 `every`メソッドの呼び出し、`callbackfn`の各要素に対して関数`array1`まで、`callbackfn`返します`false`、または配列の末尾までです。|  
|`thisArg`|省略可能です。 `this` のキーワードが `callbackfn` 関数内で参照できるオブジェクト。 `thisArg` を省略すると、`undefined` が `this` 値として使用されます。|  
  
## <a name="return-value"></a>戻り値  
 `true`場合、`callbackfn`関数が返される`true`のすべての配列の要素。 それ以外の場合、`false`です。 配列の要素を持たない場合、`every`メソッドを返します。`true`です。  
  
## <a name="exceptions"></a>例外  
 `callbackfn` 引数が関数オブジェクトではない場合は、`TypeError` 例外がスローされます。  
  
## <a name="remarks"></a>コメント  
 `every`メソッドの呼び出し、`callbackfn`関数を昇順でインデックス、まで、配列の要素ごとに 1 回、`callbackfn`関数が返される`false`です。 場合の原因となる要素`callbackfn`を返す`false`が見つかると、`every`メソッドが直ちに返されます`false`です。 それ以外の場合、`every`メソッドを返します。`true`です。  
  
 配列内で欠落している要素に対しては、コールバック関数は呼び出されません。  
  
 配列オブジェクトに加えて、`every` メソッドは、`length` プロパティを持つオブジェクトおよび数値インデックス付きプロパティ名を持つオブジェクトで使用できます。  
  
> [!NOTE]
>  使用することができます、 [some メソッド (Array)](../../javascript/reference/some-method-array-javascript.md)コールバック関数が返すかどうかを確認する`true`任意配列の要素。  
  
## <a name="callback-function-syntax"></a>コールバック関数の構文  
 コールバック関数の構文は次のとおりです。  
  
 `function callbackfn(value, index, array1)`  
  
 最大 3 つのパラメーターを使用して、コールバック関数を宣言することができます。  
  
 コールバック関数パラメーターの一覧を次の表に示します。  
  
|コールバック パラメーター|定義|  
|------------------------|----------------|  
|`value`|配列の要素の値。|  
|`index`|配列要素の数値インデックス。|  
|`array1`|要素を格納している配列オブジェクト。|  
  
## <a name="modifying-the-array-object"></a>配列オブジェクトの変更  
 配列オブジェクトはコールバック関数で変更できます。  
  
 `every` メソッドの開始後に配列オブジェクトを変更した結果を次の表に示します。  
  
|`every` メソッドの開始後の条件|要素がコールバック関数に渡されるか?|  
|-----------------------------------------------|------------------------------------------|  
|要素が配列の元の長さを越えて追加されている。|いいえ。|  
|要素はが、配列内の欠落した要素を補うために追加されている。|はい (そのインデックスがまだコールバック関数に渡されていない場合)。|  
|要素が変更されている。|はい (その要素がまだコールバック関数に渡されていない場合)。|  
|要素が配列から削除されている。|いいえ (その要素が既にコールバック関数に渡されている場合を除く)。|  
  
## <a name="example"></a>例  
 `every` メソッドの使用例を次に示します。  
  
```JavaScript  
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
  
## <a name="example"></a>例  
 `thisArg` キーワードで参照できるオブジェクトを指定する `this` 引数の使用例を次に示します。  
  
```JavaScript  
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
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [some メソッド (Array)](../../javascript/reference/some-method-array-javascript.md)   
 [filter メソッド (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Array オブジェクト](../../javascript/reference/array-object-javascript.md)   
 [配列の使用](../../javascript/advanced/using-arrays-javascript.md)