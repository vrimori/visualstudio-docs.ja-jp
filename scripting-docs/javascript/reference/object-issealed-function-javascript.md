---
title: "Object.isSealed 関数 (JavaScript) | Microsoft Docs"
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
  - "isSealed 関数 [JavaScript]"
  - "Object.isSealed [JavaScript]"
  - "プロパティ [JavaScript], 属性のロック"
ms.assetid: af4f192e-cebe-44b9-8eef-90c096f5ae8f
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Object.isSealed 関数 (JavaScript)
オブジェクトの既存のプロパティ属性および値を変更できず、オブジェクトへの新しいプロパティの追加もできない場合は、`true` を返します。  
  
## 構文  
  
```javascript  
Object.isSealed(object)  
```  
  
#### パラメーター  
 `object`  
 必須です。  テストするオブジェクトを指定します。  
  
## 戻り値  
 次の両方が true の場合に `true` を返します。  
  
-   オブジェクトが拡張不能である \(新しいプロパティをオブジェクトに追加できない\)。  
  
-   `configurable` 属性がすべての既存のプロパティで `false` である。  
  
 オブジェクトにプロパティがなく、オブジェクトが拡張不能な場合、関数は `true` を返します。  
  
## 例外  
 `object` 引数がオブジェクトではない場合は、`TypeError` 例外がスローされます。  
  
## 解説  
 プロパティの `configurable` 属性が `false` の場合、プロパティ属性の変更およびプロパティの削除はできません。  `writable` が `false` の場合、データ プロパティ値は変更できません。  `configurable` 属性が `false` で、`writable` 属性が `true` の場合は、`value` 属性と `writable` 属性を変更できます。  
  
 `Object.isSealed` 関数は、戻り値を確認するためにプロパティの `writable` 属性は使用しません。  
  
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
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Yes|いいえ|いいえ|  
|`Object.isSealed`|いいえ|Yes|いいえ|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|いいえ|Yes|Yes|  
  
## 使用例  
 `Object.isSealed` 関数の使用例を次に示します。  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Seal the object, and verify that it is sealed.  
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
 [Object.seal 関数](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze 関数](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible 関数](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isFrozen 関数](../../javascript/reference/object-isfrozen-function-javascript.md)   
 [Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)