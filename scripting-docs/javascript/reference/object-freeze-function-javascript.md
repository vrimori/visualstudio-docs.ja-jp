---
title: "Object.freeze 関数 (JavaScript) | Microsoft Docs"
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
  - "freeze 関数"
  - "Object.freeze 関数"
ms.assetid: 83ffe193-0a37-4e0c-9b66-44c422765fb3
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# Object.freeze 関数 (JavaScript)
既存のプロパティ属性と値の変更、および新しいプロパティの追加を防止します。  
  
## 構文  
  
```javascript  
Object.freeze(object)  
```  
  
#### パラメーター  
 `object`  
 必須です。  属性をロックするオブジェクトを指定します。  
  
## 戻り値  
 関数に渡されたオブジェクト。  
  
## 例外  
 `object` 引数がオブジェクトではない場合は、`TypeError` 例外がスローされます。  
  
## 解説  
 `Object.freeze` 関数は次の処理を行います。  
  
-   新しいプロパティを追加できないようにするために、オブジェクトを拡張不能にします。  
  
-   オブジェクトのすべてのプロパティの `configurable` 属性を `false` に設定します。  `configurable` が `false` に設定されていると、プロパティ属性の変更およびプロパティの削除ができなくなります。  
  
-   オブジェクトのすべてのデータ プロパティの `writable` 属性を`false` に設定します。  `writable` が false の場合、データ プロパティ値は変更できません。  
  
 プロパティ属性の設定方法の詳細については、「[Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)」を参照してください。  プロパティの属性を取得するには、[Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md) を使用できます。  
  
## 関連する関数  
 関連する次の関数は、オブジェクトの属性の変更を防止します。  
  
|関数|オブジェクトを拡張不能にするか|`configurable` が各プロパティで `false` に設定される|`writable` が各プロパティで `false` に設定される|  
|--------|---------------------|--------------------------------------------|----------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Yes|いいえ|いいえ|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Yes|Yes|いいえ|  
|`Object.freeze`|Yes|Yes|Yes|  
  
 次の関数は、次の表でマークされた条件がすべて当てはまる場合 `true` を返します。  
  
|関数|オブジェクトは拡張可能?|`configurable` はすべてのプロパティで `false`?|`writable` はすべてのデータ プロパティで `false`?|  
|--------|------------------|-----------------------------------------|-----------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Yes|いいえ|いいえ|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|いいえ|Yes|Yes|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|いいえ|Yes|Yes|  
  
## 使用例  
 `Object.freeze` 関数の使用例を次に示します。  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object.  
Object.freeze(obj);  
  
// Try to add a new property, and then verify that it is not added.   
    obj.newProp = 50;  
    document.write(obj.newProp);  
    document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
document.write("<br/>");  
  
// Try to change a property value, and then verify that it is not changed.   
obj.pasta = "linguini";  
document.write(obj.pasta);  
  
// Output:  
// undefined  
// 10  
// spaghetti  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 参照  
 [Object.preventExtensions 関数](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal 関数](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.isExtensible 関数](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed 関数](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen 関数](../../javascript/reference/object-isfrozen-function-javascript.md)