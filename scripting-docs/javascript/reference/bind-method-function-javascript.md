---
title: "bind メソッド (Function) (JavaScript) |Microsoft ドキュメント"
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
- parameters [JavaScript], bind method
- arguments [JavaScript], bind method
- bind method [JavaScript]
- this keyword [JavaScript], bind method
ms.assetid: 28946f47-b758-48cf-b508-610a0f2f6e19
caps.latest.revision: "21"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd7fc752df9bd41f8625ac2cb484486dfd19558d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="bind-method-function-javascript"></a>bind メソッド (Function) (JavaScript)
指定された関数に対して、元の関数と同じ本体を持つ、バインディングされた関数を作成します。 バインディングされた関数では、`this` オブジェクトは、渡されたオブジェクトに解決します。 バインディングされた関数には、指定された初期パラメーターがあります。  
  
## <a name="syntax"></a>構文  
  
```  
  
function.bind(thisArg[,arg1[,arg2[,argN]]])  
```  
  
#### <a name="parameters"></a>パラメーター  
 `function`  
 必須です。 関数オブジェクトを指定します。  
  
 `thisArg`  
 必須です。 新しい関数内で `this` キーワードが参照できるオブジェクトを指定します。  
  
 `arg1`[,`arg2`[,`argN`]]]  
 省略可能です。 新しい関数に渡す引数のリストを指定します。  
  
## <a name="return-value"></a>戻り値  
 `function` オブジェクトと初期引数以外は `thisArg` 関数と同じ新しい関数。  
  
## <a name="exceptions"></a>例外  
 指定した `function` が関数ではない場合は、`TypeError` 例外がスローされます。  
  
## <a name="example"></a>例  
 `bind` メソッドの使用例を次のコードに示します。  
  
```JavaScript  
// Define the original function.  
var checkNumericRange = function (value) {  
    if (typeof value !== 'number')  
        return false;  
    else  
        return value >= this.minimum && value <= this.maximum;  
}  
  
// The range object will become the this value in the callback function.  
var range = { minimum: 10, maximum: 20 };  
  
// Bind the checkNumericRange function.  
var boundCheckNumericRange = checkNumericRange.bind(range);  
  
// Use the new function to check whether 12 is in the numeric range.  
var result = boundCheckNumericRange (12);  
document.write(result);  
  
// Output: true  
```  
  
## <a name="example"></a>例  
 次の例では、`thisArg` オブジェクトは元のメソッドを含むオブジェクトとは異なります。  
  
```JavaScript  
// Create an object that contains the original function.  
var originalObject = {  
    minimum: 50,  
    maximum: 100,  
    checkNumericRange: function (value) {  
        if (typeof value !== 'number')  
            return false;  
        else  
            return value >= this.minimum && value <= this.maximum;  
    }  
}  
  
// Check whether 10 is in the numeric range.  
var result = originalObject.checkNumericRange(10);  
document.write(result + " ");  
// Output: false  
  
// The range object supplies the range for the bound function.  
var range = { minimum: 10, maximum: 20 };  
  
// Create a new version of the checkNumericRange function that uses range.  
var boundObjectWithRange = originalObject.checkNumericRange.bind(range);  
  
// Check whether 10 is in the numeric range.  
var result = boundObjectWithRange(10);  
document.write(result);  
// Output: true  
```  
  
## <a name="example"></a>例  
 `arg1[,arg2[,argN]]]` 引数の使用例を次のコードに示します。 バインディングされた関数は、`bind` メソッドで指定されたパラメーターを 1 番目と 2 番目のパラメーターとして使用します。 バインディングされた関数が呼び出されたときに指定されたパラメーターは、3 番目、4 番目などのパラメーターとして使用されます。  
  
```JavaScript  
// Define the original function with four parameters.  
var displayArgs = function (val1, val2, val3, val4) {  
    document.write(val1 + " " + val2 + " " + val3 + " " + val4);  
}  
  
var emptyObject = {};  
  
// Create a new function that uses the 12 and "a" parameters  
// as the first and second parameters.  
var displayArgs2 = displayArgs.bind(emptyObject, 12, "a");  
  
// Call the new function. The "b" and "c" parameters are used  
// as the third and fourth parameters.  
displayArgs2("b", "c");  
// Output: 12 a b c   
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Function オブジェクト](../../javascript/reference/function-object-javascript.md)   
 [filter メソッド (Array)](../../javascript/reference/filter-method-array-javascript.md)   
 [Bind メソッドの使用](../../javascript/advanced/using-the-bind-method-javascript.md)   
 [Hilo JavaScript のサンプル アプリ (Windows ストア)](http://hilojs.codeplex.com/SourceControl/latest)