---
title: Object.getOwnPropertyNames 関数 (JavaScript) |Microsoft ドキュメント
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
- getOwnPropertyNames method [JavaScript]
- Object.getOwnPropertyNames method [JavaScript]
ms.assetid: 59f4b6b1-02be-44b3-a06c-a5ca8f70c3d8
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 76ca0036b9dedf7b4cee7b543469939e35dfe8d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639932"
---
# <a name="objectgetownpropertynames-function-javascript"></a>Object.getOwnPropertyNames 関数 (JavaScript)
オブジェクトの独自のプロパティの名前を返します。 オブジェクトの独自のプロパティは、そのオブジェクトで直接定義され、オブジェクトのプロトタイプから継承していないされることです。 オブジェクトのプロパティには、(オブジェクト) のフィールドと関数の両方が含まれます。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
Object.getOwnPropertyNames(object)  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|定義|  
|---------------|----------------|  
|`object`|必須です。 独自のプロパティを含むオブジェクト。|  
  
## <a name="return-value"></a>戻り値  
 オブジェクトの独自のプロパティの名前を格納する配列。  
  
## <a name="exceptions"></a>例外  
 値が指定した場合、`object`引数が、オブジェクトの名前ではありません、`TypeError`例外がスローされます。  
  
## <a name="remarks"></a>コメント  
 `getOwnPropertyNames`メソッドが列挙可能でない列挙可能なプロパティとメソッドの両方の名前を返します。 列挙可能なプロパティとメソッドの名前のみを返すを使用することができます、 [Object.keys 関数](../../javascript/reference/object-keys-function-javascript.md)です。  
  
## <a name="example"></a>例  
 次の例では、3 つのプロパティとメソッドを持つオブジェクトを作成します。 次を使用して、`getOwnPropertyNames`オブジェクトの own プロパティ (メソッドを含む) を取得します。  
  
```JavaScript  
function Pasta(grain, width, shape) {  
    // Define properties.  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Get the own property names.  
var arr = Object.getOwnPropertyNames(spaghetti);  
document.write (arr);  
  
// Output:  
//   grain,width,shape,toString  
```  
  
## <a name="example"></a>例  
 次の例では、先頭文字のプロパティの名前 ' で、**スパゲッティ**でオブジェクトが構築された、**パスタ**コンス トラクターです。  
  
```JavaScript  
function Pasta(grain, size, shape) {  
    this.grain = grain;   
    this.size = size;   
    this.shape = shape;   
}  
  
var spaghetti = new Pasta("wheat", 2, "circle");  
  
var names = Object.getOwnPropertyNames(spaghetti).filter(CheckKey);  
document.write(names);   
  
// Check whether the first character of a string is 's'.   
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);   
    if (firstChar.toLowerCase() == 's')  
        return true;   
    else  
         return false;   
}  
// Output:  
// size,shape  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Object.keys 関数](../../javascript/reference/object-keys-function-javascript.md)