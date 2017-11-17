---
title: "some メソッド (Array) (JavaScript) |Microsoft ドキュメント"
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
- arrays [JavaScript], some method
- some method [JavaScript]
ms.assetid: 7b6822f9-c406-4f4e-bfec-a93459745992
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba3f855c61daac511bcf7aca6b47f643dda93313
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="some-method-array-javascript"></a>some メソッド (Array) (JavaScript)
指定されたコールバック関数を返すかどうかを決定`true`任意配列の要素。  
  
## <a name="syntax"></a>構文  
  
```  
  
array1.some(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|定義|  
|---------------|----------------|  
|`array1`|必須です。 配列オブジェクト。|  
|`callbackfn`|必須です。 3 つまでの引数を受け取る関数。 `some`メソッドの呼び出し、`callbackfn`の各要素に対して関数`array1`まで、`callbackfn`返します`true`、または配列の末尾までです。|  
|`thisArg`|省略可能です。 `this` のキーワードが `callbackfn` 関数内で参照できるオブジェクト。 `thisArg` を省略すると、`undefined` が `this` 値として使用されます。|  
  
## <a name="return-value"></a>戻り値  
 `true`場合、`callbackfn`関数が返される`true`任意の配列要素です。 それ以外の場合、`false`です。  
  
## <a name="exceptions"></a>例外  
 `callbackfn` 引数が関数オブジェクトではない場合は、`TypeError` 例外がスローされます。  
  
## <a name="remarks"></a>コメント  
 `some`メソッドの呼び出し、`callbackfn`昇順のインデックス、まで各配列要素に対して関数、`callbackfn`関数が返される`true`です。 場合の原因となる要素`callbackfn`を返す`true`が見つかると、`some`メソッドが直ちに返されます`true`です。 コールバックが返されない場合は`true`任意の要素で、`some`メソッドを返します。`false`です。  
  
 配列内で欠落している要素に対しては、コールバック関数は呼び出されません。  
  
 配列オブジェクトに加えて、`some` メソッドは、`length` プロパティを持つオブジェクトおよび数値インデックス付きプロパティ名を持つオブジェクトで使用できます。  
  
> [!NOTE]
>  使用することができます、 [every メソッド (Array)](../../javascript/reference/every-method-array-javascript.md)コールバック関数が返すかどうかを確認する`true`のすべての要素の配列。  
  
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
  
 `some` メソッドの開始後に配列オブジェクトを変更した結果を次の表に示します。  
  
|`some` メソッドの開始後の条件|要素がコールバック関数に渡されるか?|  
|----------------------------------------------|------------------------------------------|  
|要素が配列の元の長さを越えて追加されている。|いいえ。|  
|要素はが、配列内の欠落した要素を補うために追加されている。|はい (そのインデックスがまだコールバック関数に渡されていない場合)。|  
|要素が変更されている。|はい (その要素がまだコールバック関数に渡されていない場合)。|  
|要素が配列から削除されている。|いいえ (その要素が既にコールバック関数に渡されている場合を除く)。|  
  
## <a name="example"></a>例  
 次の例では、`some`要素を検索するかどうかを配列内のメソッドがあってもします。  
  
```JavaScript  
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
  
## <a name="example"></a>例  
 次の例を使用する方法を示しています、`thisArg`オブジェクトを指定するパラメーター、`this`キーワードで参照できます。 配列内の数値のいずれかに渡されるオブジェクトによって提供される範囲外するかどうかを確認します。  
  
```JavaScript  
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
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [every メソッド (Array)](../../javascript/reference/every-method-array-javascript.md)   
 [filter メソッド (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [map メソッド (Array)](../../javascript/reference/map-method-array-javascript.md)