---
title: "オブジェクトの反映 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1df74f34-2eb4-42f1-a930-b943c86daa0e
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# オブジェクトの反映 (JavaScript)
インターセプトされた操作で使用するメソッドを提供します。  
  
## 構文  
  
```  
Reflect.[method]  
```  
  
#### パラメーター  
 `method`  
 必須です。  `Reflect` オブジェクトのメソッドの 1 つの名前です。  
  
## 解説  
 Reflect オブジェクトを `new` 演算子でインスタンス化することはできません。  
  
 Reflect メソッドは、[プロキシ](../../javascript/reference/proxy-object-javascript.md)と共によく使用されます。プロキシは、コード内で既定の動作を実装することなく、既定の動作に委任することができるためです。  
  
 Reflect は、各プロキシ トラップと同じ名前の静的メソッドを提供します。  表の説明は完全なものではありません。  
  
|メソッド|説明|  
|----------|--------|  
|`Reflect.apply(target, thisArg, args)`|Function オブジェクトの [apply](../../javascript/reference/apply-method-function-javascript.md) メソッドと類似しています。|  
|`Reflect.construct(target, args)`|`new` 演算子に相当する関数です。|  
|`Reflect.defineProperty(target, propertyName, descriptor)`|[Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md) と類似しています。  呼び出しが成功したかどうかを示すブール値を返します。|  
|`Reflect.deleteProperty(target, propertyName)`|`delete` ステートメントと類似しています。  呼び出しが成功したかどうかを示すブール値を返します。|  
|`Reflect.enumerate(target)`|[for…in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) ステートメント、[Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md)、[Object.keys](../../javascript/reference/object-keys-function-javascript.md) 関数、および [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md) と類似しています。|  
|`Reflect.get(target, propertyName, receiver)`|すべての [getter](../../javascript/creating-objects-javascript.md) プロパティに相当する関数です。|  
|`Reflect.getOwnPropertyDescriptor(target, propertyName)`|[Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md) と類似しています。  呼び出しが成功したかどうかを示すブール値を返します。|  
|`Reflect.getPrototypeOf(target)`|[Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md) と類似しています。|  
|`Reflect.has(target, propertyName)`|`in` 演算子、[hasOwnProperty メソッド \(Object\)](../../javascript/reference/hasownproperty-method-object-javascript.md)、およびその他のメソッドと類似しています。  呼び出しが成功したかどうかを示すブール値を返します。|  
|`Reflect.isExtensible(target)`|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md) と類似しています。|  
|`Reflect.ownKeys(target)`|[Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md) と類似しています。|  
|`Reflect.preventExtensions(target)`|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md) と類似しています  呼び出しが成功したかどうかを示すブール値を返します。|  
|`Reflect.set(target, propertyName, value, receiver)`|[setter](../../javascript/creating-objects-javascript.md) プロパティの使用と類似しています。  呼び出しが成功したかどうかを示すブール値を返します。|  
|`Reflect.setPrototypeOf(target, prototype)`|[Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md) と類似しています。  呼び出しが成功したかどうかを示すブール値を返します。|  
  
## 使用例  
 次のコードの例は、アンダースコアで始まるプロパティの取得操作をブロックするプロキシを作成するために、`Reflect.get` を使用する方法を示します。  
  
```javascript  
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
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]