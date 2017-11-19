---
title: "オブジェクト (JavaScript) の反映 |Microsoft ドキュメント"
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
ms.assetid: 1df74f34-2eb4-42f1-a930-b943c86daa0e
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3574c54ee7ff69f56951cd7f4c9a93cac5275fc1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="reflect-object-javascript"></a>オブジェクトの反映 (JavaScript)
インターセプトされた操作で使用するメソッドを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
Reflect.[method]  
```  
  
#### <a name="parameters"></a>パラメーター  
 `method`  
 必ず指定します。 `Reflect` オブジェクトのメソッドの 1 つの名前です。  
  
## <a name="remarks"></a>コメント  
 Reflect オブジェクトを `new` 演算子でインスタンス化することはできません。  
  
 メソッドが子と共によく使用反映[プロキシ](../../javascript/reference/proxy-object-javascript.md)コードで、既定の動作を実装することがなく、既定の動作に委任することができるためです。  
  
 Reflect は、各プロキシ トラップと同じ名前の静的メソッドを提供します。 表の説明は完全なものではありません。  
  
|メソッド|説明|  
|------------|-----------------|  
|`Reflect.apply(target, thisArg, args)`|ような[適用](../../javascript/reference/apply-method-function-javascript.md)関数オブジェクトのメソッドです。|  
|`Reflect.construct(target, args)`|`new` 演算子に相当する関数です。|  
|`Reflect.defineProperty(target, propertyName, descriptor)`|ような[Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)です。 呼び出しが成功したかどうかを示すブール値を返します。|  
|`Reflect.deleteProperty(target, propertyName)`|`delete` ステートメントと類似しています。 呼び出しが成功したかどうかを示すブール値を返します。|  
|`Reflect.enumerate(target)`|ような[データ型.. で](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)ステートメントでは、 [Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md)、 [Object.keys](../../javascript/reference/object-keys-function-javascript.md)関数、および[JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)です。|  
|`Reflect.get(target, propertyName, receiver)`|いずれかに相当する関数[get アクセス操作子](../../javascript/creating-objects-javascript.md)プロパティです。|  
|`Reflect.getOwnPropertyDescriptor(target, propertyName)`|ような[Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)です。 呼び出しが成功したかどうかを示すブール値を返します。|  
|`Reflect.getPrototypeOf(target)`|ような[Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)です。|  
|`Reflect.has(target, propertyName)`|ような`in`演算子、 [hasOwnProperty メソッド (Object)](../../javascript/reference/hasownproperty-method-object-javascript.md)、およびその他のメソッドです。 呼び出しが成功したかどうかを示すブール値を返します。|  
|`Reflect.isExtensible(target)`|ような[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)です。|  
|`Reflect.ownKeys(target)`|ような[Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)です。|  
|`Reflect.preventExtensions(target)`|ような[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)です。 呼び出しが成功したかどうかを示すブール値を返します。|  
|`Reflect.set(target, propertyName, value, receiver)`|いずれかの方法に似ています[set アクセス操作子](../../javascript/creating-objects-javascript.md)プロパティです。 呼び出しが成功したかどうかを示すブール値を返します。|  
|`Reflect.setPrototypeOf(target, prototype)`|ような[Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md)です。 呼び出しが成功したかどうかを示すブール値を返します。|  
  
## <a name="example"></a>例  
 次のコードの例は、アンダースコアで始まるプロパティの取得操作をブロックするプロキシを作成するために、`Reflect.get` を使用する方法を示します。  
  
```JavaScript  
var p = new Proxy({}, {  
    get(k, t, r) {  
        // return undefined if key begins with underscore  
        if(k[0] === '_') return undefined;  
  
       // otherwise do default behavior  
       return Reflect.get(k, t, r);  
    }  
});  
  
p._foo = 1;  
console.log(p._foo);  
  
p.foo = 1;  
console.log(p.foo);  
  
// Output:  
// undefined  
// 1  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]