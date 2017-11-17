---
title: "Object.create 関数 (JavaScript) |Microsoft ドキュメント"
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
- create function [JavaScript]
- Object.create function [JavaScript]
ms.assetid: 0ad31f36-a9ee-444e-b0fe-c87843d03196
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f359908c5c836743e22390580f542df27d7b98e7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="objectcreate-function-javascript"></a>Object.create 関数 (JavaScript)
指定されたプロトタイプを持ち、指定されたプロパティを含む (オプション) オブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
Object.create(prototype, descriptors)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `prototype`  
 必須です。 プロトタイプとして使用するオブジェクト。 `null` でもかまいません。  
  
 `descriptors`  
 省略可能です。 1 つ以上のプロパティ記述子を含む [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] オブジェクト。  
  
 *データ プロパティ*は、値を取得および設定できるプロパティです。 データ プロパティ記述子には、`value` 属性、`writable` 属性、`enumerable` 属性、`configurable` 属性が含まれています。 最後の 3 つの属性は、指定されていない場合、既定で `false` に設定されます。 *アクセサー プロパティ*ユーザー指定の関数を呼び出すたびに、値を取得または設定します。 アクセサー プロパティ記述子には、`set` 属性、`get` 属性、またはその両方が含まれます。 詳細については、次を参照してください。 [Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)です。  
  
## <a name="return-value"></a>戻り値  
 指定された内部プロトタイプを持ち、指定されたプロパティ (存在する場合) を含む新しいオブジェクトを作成します。  
  
## <a name="exceptions"></a>例外  
 `TypeError` 例外は、以下のいずれかの条件が当てはまる場合にスローされます。  
  
-   `prototype` 引数がオブジェクトではなく、`null` でもない。  
  
-   `descriptors` 引数の記述子に `value` 属性または `writable` 属性があり、`get` 属性または `set` 属性がある。  
  
-   `descriptors` 引数の記述子に、関数ではない `get` 属性または `set` 属性がある。  
  
## <a name="remarks"></a>コメント  
 使用してこの関数を使用することができます、`null``prototype`プロトタイプ チェーンを停止するのにはパラメーター。 作成されるオブジェクトにはプロトタイプはありません。  
  
## <a name="example"></a>例  
 次の例は `null` プロトタイプを使用してオブジェクトを作成し、列挙可能なプロパティを 2 種類追加します。  
  
```JavaScript  
var newObj = Object.create(null, {  
            size: {  
                value: "large",  
                enumerable: true  
            },  
            shape: {  
                value: "round",  
                enumerable: true  
            }  
        });  
  
document.write(newObj.size + "<br/>");  
document.write(newObj.shape + "<br/>");  
document.write(Object.getPrototypeOf(newObj));  
  
// Output:  
// large  
// round  
// null  
  
```  
  
## <a name="example"></a>例  
 次の例は、Object オブジェクトと同じ内部プロトタイプを持つオブジェクトを作成します。 オブジェクト リテラルを使用して作成されたオブジェクトと同じプロトタイプがあることを確認できます。 [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)関数は、元のオブジェクトのプロトタイプを取得します。 オブジェクトのプロパティ記述子を取得するを使用することができます[Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)です。  
  
```JavaScript  
var firstLine = { x: undefined, y: undefined };  
  
var secondLine = Object.create(Object.prototype, {  
        x: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            },  
            y: {  
                value: undefined,   
                writable: true,   
                configurable: true,   
                enumerable: true  
            }  
});  
  
document.write("first line prototype = " + Object.getPrototypeOf(firstLine));  
document.write("<br/>");  
document.write("second line prototype = " + Object.getPrototypeOf(secondLine));  
  
// Output:  
// first line prototype = [object Object]  
// second line prototype = [object Object]  
```  
  
## <a name="example"></a>例  
 次の例は、Shape オブジェクトと同じ内部プロトタイプを持つオブジェクトを作成します。  
  
```JavaScript  
  
// Create the shape object.  
var Shape = { twoDimensional: true, color: undefined, hasLineSegments: undefined };  
  
var Square = Object.create(Object.getPrototypeOf(Shape));  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Object.getPrototypeOf 関数](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [isPrototypeOf メソッド (Object)](../../javascript/reference/isprototypeof-method-object-javascript.md)   
 [オブジェクトの作成](../../javascript/creating-objects-javascript.md)