---
title: "Proxy オブジェクト (JavaScript) | Microsoft Docs"
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
ms.assetid: 2b89abee-04fa-47e6-9676-980016cff5f8
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Proxy オブジェクト (JavaScript)
オブジェクトのカスタム動作を有効にします。  
  
## 構文  
  
```  
proxyObj = new Proxy(target, handler)  
```  
  
#### パラメーター  
 `target`  
 必須。  プロキシによって仮想化するオブジェクトまたは関数。  
  
 `handler`  
 必須。  カスタム動作を実装するメソッド \(トラップ\) を持つオブジェクト。  
  
## 解説  
 `Proxy` オブジェクトは、別のオブジェクトにおける内部の低水準操作を傍受するために使用します。  Proxy オブジェクトは、傍受、オブジェクトの仮想化、ログ記録\/プロファイル作成、および他の目的で使用できます。  
  
 特定の操作についてのトラップがプロキシのハンドラーで定義されていない場合、操作はターゲットに転送されます。  
  
 Handler オブジェクトは、カスタム動作を実装する以下のメソッド \(トラップ\) を定義します。  例にはすべてが記載されているわけではありません。  Handler メソッドで条件付きの既定の動作をサポートするには、[オブジェクトの反映](../../javascript/reference/reflect-object-javascript.md) のメソッドを使用します。  
  
|Handler メソッド \(トラップ\) の構文|使用例|  
|-------------------------------|---------|  
|`apply: function(target, thisArg, args)`|関数呼び出しのトラップ。|  
|`construct: function(target, args)`|コンストラクターのトラップ。|  
|`defineProperty: function(target, propertyName, descriptor)`|[Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md) のトラップ。|  
|`deleteProperty: function(target, propertyName)`|`delete` ステートメントのトラップ。|  
|`enumerate: function(target)`|[for…in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md) ステートメント、[Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md)、[Object.keys](../../javascript/reference/object-keys-function-javascript.md) 関数、[JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md) のトラップ。|  
|`get: function(target, propertyName, receiver)`|任意の [getter](../../javascript/creating-objects-javascript.md) のプロパティのトラップ。|  
|`getOwnPropertyDescriptor: function(target, propertyName)`|[Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md) のトラップ。|  
|`getPrototypeOf: function(target)`|[Object.getPrototypeOf 関数](../../javascript/reference/object-getprototypeof-function-javascript.md) のトラップ。|  
|`has: function(target, propertyName)`|`in` 演算子、[hasOwnProperty メソッド \(Object\)](../../javascript/reference/hasownproperty-method-object-javascript.md)、および他のメソッドのトラップ。|  
|`isExtensible: function(target)`|[Object.isExtensible 関数](../../javascript/reference/object-isextensible-function-javascript.md) のトラップ。|  
|`ownKeys: function(target)`|[Object.getOwnPropertyNames 関数](../../javascript/reference/object-getownpropertynames-function-javascript.md) のトラップ。|  
|`preventExtensions: function(target)`|[Object.preventExtensions 関数](../../javascript/reference/object-preventextensions-function-javascript.md) のトラップ。|  
|`set: function(target, propertyName, value, receiver)`|任意の [setter](../../javascript/creating-objects-javascript.md) のプロパティのトラップ。|  
|`setPrototypeOf: function(target, prototype)`|[Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md) のトラップ。|  
  
## 使用例  
 次のコード例は、`get` トラップを使用してオブジェクト リテラルのプロキシを作成する方法を示しています。  
  
```javascript  
var target = {};  
var handler = {  
  get: function (receiver, name) {  
    // This example includes a template string.  
    return `Hello, ${name}!`;  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(p.world);  
  
// Output:  
// Hello, world!  
  
```  
  
## 使用例  
 次のコード例は、`apply` トラップを使用して関数のプロキシを作成する方法を示しています。  
  
```javascript  
var target = function () { return 'I am the target'; };  
var handler = {  
  // This example includes a rest parameter.  
  apply: function (receiver, ...args) {  
    return 'I am the proxy';  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(target()):  
console.log(p()):  
  
// Output:  
// I am the target  
// I am the proxy  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]