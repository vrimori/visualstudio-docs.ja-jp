---
title: "Object.isExtensible 関数 (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "isExtensible 関数 [JavaScript]"
  - "Object.isExtensible 関数 [JavaScript]"
ms.assetid: a7d10beb-0d01-4e2d-8263-59ff07ac4352
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Object.isExtensible 関数 (JavaScript)
新しいプロパティをオブジェクトに追加できるかどうかを示す値を返します。  
  
## 構文  
  
```javascript  
Object.isExtensible(object)  
```  
  
#### パラメーター  
 `object`  
 必須です。  テストするオブジェクトを指定します。  
  
## 戻り値  
 オブジェクトが拡張可能な場合は `true`、それ以外の場合は `false` を返します。  
  
## 例外  
 `object` 引数がオブジェクトではない場合は、`TypeError` 例外がスローされます。  
  
## 解説  
 プロパティ属性の設定方法の詳細については、「[Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)」を参照してください。  プロパティの属性を取得するには、[Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md) を使用できます。  
  
## 関連する関数  
 関連する次の関数は、オブジェクトの属性の変更を防止します。  
  
|関数|オブジェクトを拡張不能にするか|`configurable` が各プロパティで `false` に設定される|`writable` が各プロパティで `false` に設定される|  
|--------|---------------------|--------------------------------------------|----------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Yes|いいえ|いいえ|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Yes|Yes|いいえ|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Yes|Yes|Yes|  
  
 次の関数は、次の表でマークされた条件がすべて当てはまる場合 `true` を返します。  
  
|関数|オブジェクトは拡張可能?|`configurable` はすべてのプロパティで `false`?|`writable` はすべてのデータ プロパティで `false`?|  
|--------|------------------|-----------------------------------------|-----------------------------------------|  
|`Object.isExtensible`|Yes|いいえ|いいえ|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|いいえ|Yes|いいえ|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|いいえ|Yes|Yes|  
  
## 使用例  
 `Object.isExtensible` 関数の使用例を次に示します。  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
undefined  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 参照  
 [Object.preventExtensions 関数](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal 関数](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze 関数](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isSealed 関数](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen 関数](../../javascript/reference/object-isfrozen-function-javascript.md)