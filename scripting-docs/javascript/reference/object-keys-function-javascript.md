---
title: "Object.keys 関数 (JavaScript) |Microsoft ドキュメント"
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
- Object.keys method [JavaScript]
- keys method [JavaScript]
ms.assetid: cf4a7daf-cf28-4467-bc6b-f7f106ec3876
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0e725c3ab7206b04d9a900cb614b57c37dfc4351
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="objectkeys-function-javascript"></a>Object.keys 関数 (JavaScript)
オブジェクトの列挙可能なプロパティおよびメソッドの名前を返します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
Object.keys(object)  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|定義|  
|---------------|----------------|  
|`object`|必須です。 プロパティとメソッドを格納するオブジェクト。 これには、作成したオブジェクトまたは既存のドキュメント オブジェクト モデル (DOM) オブジェクトを指定できます。|  
  
## <a name="return-value"></a>戻り値  
 列挙可能なプロパティの名前と、オブジェクトのメソッドを格納する配列。  
  
## <a name="exceptions"></a>例外  
 値が指定した場合、`object`引数が、オブジェクトの名前ではありません、`TypeError`例外がスローされます。  
  
## <a name="remarks"></a>コメント  
 `keys`メソッドが列挙可能なプロパティとメソッドの名前のみを返します。 列挙可能でない列挙可能なプロパティとメソッドの両方の名前を返すを使用することができます[Object.getOwnPropertyNames 関数](../../javascript/reference/object-getownpropertynames-function-javascript.md)です。  
  
 については、`enumerable`属性、プロパティの次を参照してください。 [Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)と[Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)です。  
  
## <a name="example"></a>例  
 次の例では、3 つのプロパティとメソッドを持つオブジェクトを作成します。 次を使用して、`keys`プロパティと、オブジェクトのメソッドを取得します。  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
  
    // Define a method.  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Put the enumerable properties and methods of the object in an array.  
var arr = Object.keys(spaghetti);  
document.write (arr);  
  
// Output:  
// grain,width,shape,toString  
```  
  
## <a name="example"></a>例  
 次の例では、"g"パスタ オブジェクト内の文字で始まるすべての列挙可能なプロパティの名前を表示します。  
  
```JavaScript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
}  
  
var polenta = new Pasta("corn", 1, "mush");  
  
var keys = Object.keys(polenta).filter(CheckKey);  
document.write(keys);  
  
// Check whether the first character of a string is "g".  
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);  
    if (firstChar.toLowerCase() == "g")  
        return true;  
    else  
        return false;  
}  
  
// Output:  
// grain  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Object.getOwnPropertyNames 関数](../../javascript/reference/object-getownpropertynames-function-javascript.md)