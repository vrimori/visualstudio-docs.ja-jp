---
title: Proxy オブジェクト (JavaScript) |Microsoft ドキュメント
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
ms.assetid: 2b89abee-04fa-47e6-9676-980016cff5f8
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4ee75310f1d976e0a0896b1be34a80c594cdd054
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
ms.locfileid: "29899598"
---
# <a name="proxy-object-javascript"></a>Proxy オブジェクト (JavaScript)
オブジェクトのカスタム動作を有効にします。  
  
## <a name="syntax"></a>構文  
  
```  
proxyObj = new Proxy(target, handler)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `target`  
 必須。 プロキシによって仮想化するオブジェクトまたは関数。  
  
 `handler`  
 必須。 カスタム動作を実装するメソッド (トラップ) を持つオブジェクト。  
  
## <a name="remarks"></a>コメント  
 `Proxy` オブジェクトは、別のオブジェクトにおける内部の低水準操作を傍受するために使用します。 Proxy オブジェクトは、傍受、オブジェクトの仮想化、ログ記録/プロファイル作成、および他の目的で使用できます。  
  
 特定の操作についてのトラップがプロキシのハンドラーで定義されていない場合、操作はターゲットに転送されます。  
  
 Handler オブジェクトは、カスタム動作を実装する以下のメソッド (トラップ) を定義します。 例にはすべてが記載されているわけではありません。 ハンドラー メソッドで条件付きの既定の動作をサポートするためのメソッドを使用して[オブジェクトの反映](../../javascript/reference/reflect-object-javascript.md)です。  
  
|Handler メソッド (トラップ) の構文|使用例|  
|------------------------------------|-----------------------|  
|`apply: function(target, thisArg, args)`|関数呼び出しのトラップ。|  
|`construct: function(target, args)`|コンストラクターのトラップ。|  
|`defineProperty: function(target, propertyName, descriptor)`|トラップ[Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)です。|  
|`deleteProperty: function(target, propertyName)`|`delete` ステートメントのトラップ。|  
|`enumerate: function(target)`|トラップ、[データ型 で](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)ステートメントでは、 [Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md)、 [Object.keys](../../javascript/reference/object-keys-function-javascript.md)関数、および[JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)です。|  
|`get: function(target, propertyName, receiver)`|いずれかのトラップ[get アクセス操作子](../../javascript/creating-objects-javascript.md)プロパティです。|  
|`getOwnPropertyDescriptor: function(target, propertyName)`|トラップ[Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)です。|  
|`getPrototypeOf: function(target)`|トラップ[Object.getPrototypeOf 関数](../../javascript/reference/object-getprototypeof-function-javascript.md)です。|  
|`has: function(target, propertyName)`|トラップ、`in`演算子、 [hasOwnProperty メソッド (Object)](../../javascript/reference/hasownproperty-method-object-javascript.md)、およびその他のメソッドです。|  
|`isExtensible: function(target)`|トラップ[Object.isExtensible 関数](../../javascript/reference/object-isextensible-function-javascript.md)です。|  
|`ownKeys: function(target)`|トラップ[Object.getOwnPropertyNames 関数](../../javascript/reference/object-getownpropertynames-function-javascript.md)です。|  
|`preventExtensions: function(target)`|トラップ[Object.preventExtensions 関数](../../javascript/reference/object-preventextensions-function-javascript.md)です。|  
|`set: function(target, propertyName, value, receiver)`|いずれかのトラップ[set アクセス操作子](../../javascript/creating-objects-javascript.md)プロパティです。|  
|`setPrototypeOf: function(target, prototype)`|トラップ[Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md)です。|  
  
## <a name="example"></a>例  
 次のコード例は、`get` トラップを使用してオブジェクト リテラルのプロキシを作成する方法を示しています。  
  
```JavaScript  
var target = {};  
var handler = {  
  get: function (target, property, receiver) {  
    // This example includes a template string.  
    return `Hello, ${property}!`;  
  }  
};  
  
var p = new Proxy(target, handler);  
console.log(p.world);  
  
// Output:  
// Hello, world!  
  
```  
  
## <a name="example"></a>例  
 次のコード例は、`apply` トラップを使用して関数のプロキシを作成する方法を示しています。  
  
```JavaScript  
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
  
## <a name="requirements"></a>必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
