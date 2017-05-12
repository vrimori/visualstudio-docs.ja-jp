---
title: "Object.preventExtensions 関数 (JavaScript) | Microsoft Docs"
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
  - "Object.preventExtensions 関数 [JavaScript]"
  - "preventExtensions 関数 [JavaScript]"
  - "新しいプロパティの防止 [JavaScript]"
  - "プロパティ [JavaScript], 防止 (新規)"
ms.assetid: e6b48197-2374-4437-a9fe-519dd45a2077
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Object.preventExtensions 関数 (JavaScript)
オブジェクトへの新しいプロパティの追加を防止します。  
  
## 構文  
  
```javascript  
Object.preventExtensions(object)  
```  
  
#### パラメーター  
 `object`  
 必須です。  拡張不能にするオブジェクトを指定します。  
  
## 戻り値  
 関数に渡されたオブジェクト。  
  
## 例外  
 `object` 引数がオブジェクトではない場合は、`TypeError` 例外がスローされます。  
  
## 解説  
 `Object.preventExtensions` 関数は、新しいプロパティを追加できないようにするために、オブジェクトを拡張不能にします。  拡張不能にしたオブジェクトを拡張可能にすることはできません。  
  
 プロパティ属性の設定方法の詳細については、「[Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)」を参照してください。  
  
## 関連する関数  
 関連する次の関数は、オブジェクトの属性の変更を防止します。  
  
|関数|オブジェクトを拡張不能にするか|`configurable` が各プロパティで `false` に設定される|`writable` が各プロパティで `false` に設定される|  
|--------|---------------------|--------------------------------------------|----------------------------------------|  
|`Object.preventExtensions`|Yes|いいえ|いいえ|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Yes|Yes|いいえ|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Yes|Yes|Yes|  
  
 次の関数は、次の表でマークされた条件がすべて当てはまる場合 `true` を返します。  
  
|関数|オブジェクトは拡張可能?|`configurable` はすべてのプロパティで `false`?|`writable` はすべてのデータ プロパティで `false`?|  
|--------|------------------|-----------------------------------------|-----------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Yes|いいえ|いいえ|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|いいえ|Yes|いいえ|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|いいえ|Yes|Yes|  
  
## 使用例  
 `Object.preventExtensions` 関数の使用例を次に示します。  
  
```javascript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
document.write(Object.isExtensible(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
// false  
// undefined  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 参照  
 [Object.seal 関数](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze 関数](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible 関数](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed 関数](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen 関数](../../javascript/reference/object-isfrozen-function-javascript.md)