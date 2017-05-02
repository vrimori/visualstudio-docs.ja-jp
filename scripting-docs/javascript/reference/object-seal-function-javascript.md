---
title: "Object.seal 関数 (JavaScript) | Microsoft Docs"
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
  - "Object.seal 関数"
  - "seal 関数"
ms.assetid: e72c804a-4dab-4ec9-b9df-9c9c908aa12d
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Object.seal 関数 (JavaScript)
既存のプロパティの属性の変更、および新しいプロパティの追加を防止します。  
  
## 構文  
  
```javascript  
Object.seal(object)  
```  
  
#### パラメーター  
 `object`  
 必須です。  属性をロックするオブジェクトを指定します。  
  
## 戻り値  
 関数に渡されたオブジェクト。  
  
## 例外  
 `object` 引数がオブジェクトではない場合は、`TypeError` 例外がスローされます。  
  
## 解説  
 `Object.seal` 関数は次の両方の処理を行います。  
  
-   新しいプロパティを追加できないようにするために、オブジェクトを拡張不能にします。  
  
-   オブジェクトのすべてのプロパティの `configurable` 属性を `false` に設定します。  
  
 `configurable` 属性が `false` の場合、プロパティ属性の変更およびプロパティの削除ができなくなります。  `configurable` 属性が `false` で、`writable` 属性が `true` の場合は、`value` 属性と `writable` 属性を変更できます。  
  
 `Object.seal`関数は `writable` 属性を変更しません。  
  
 プロパティ属性の設定方法の詳細については、「[Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)」を参照してください。  プロパティの属性を取得するには、[Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md) を使用できます。  
  
## 関連する関数  
 関連する次の関数は、オブジェクトの属性の変更を防止します。  
  
|関数|オブジェクトを拡張不能にするか|`configurable` が各プロパティで `false` に設定される|`writable` が各プロパティで `false` に設定される|  
|--------|---------------------|--------------------------------------------|----------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Yes|いいえ|いいえ|  
|`Object.seal`|Yes|Yes|いいえ|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Yes|Yes|Yes|  
  
 次の関数は、次の表でマークされた条件がすべて当てはまる場合 `true` を返します。  
  
|関数|オブジェクトは拡張可能?|`configurable` はすべてのプロパティで `false`?|`writable` はすべてのデータ プロパティで `false`?|  
|--------|------------------|-----------------------------------------|-----------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Yes|いいえ|いいえ|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|いいえ|Yes|いいえ|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|いいえ|Yes|Yes|  
  
## 使用例  
 `Object.seal` 関数の使用例を次に示します。  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
// Seal the object.  
Object.seal(obj);  
document.write(Object.isSealed(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write(obj.newProp);  
document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
  
// Output:  
// true  
// undefined  
// 10  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 参照  
 [Object.preventExtensions 関数](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.freeze 関数](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible 関数](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed 関数](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen 関数](../../javascript/reference/object-isfrozen-function-javascript.md)