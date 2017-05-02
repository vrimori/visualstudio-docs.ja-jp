---
title: "Object.create 関数 (JavaScript) | Microsoft Docs"
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
  - "create 関数 [JavaScript]"
  - "Object.create 関数 [JavaScript]"
ms.assetid: 0ad31f36-a9ee-444e-b0fe-c87843d03196
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Object.create 関数 (JavaScript)
指定されたプロトタイプを持ち、指定されたプロパティを含む \(オプション\) オブジェクトを作成します。  
  
## 構文  
  
```  
Object.create(prototype, descriptors)  
```  
  
#### パラメーター  
 `prototype`  
 必須。  プロトタイプとして使用するオブジェクト。  `null` でもかまいません。  
  
 `descriptors`  
 省略可能。  1 つ以上のプロパティ記述子を含む [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] オブジェクト。  
  
 *データ プロパティ*は、値を取得および設定できるプロパティです。  データ プロパティ記述子には、`value` 属性、`writable` 属性、`enumerable` 属性、`configurable` 属性が含まれています。  最後の 3 つの属性は、指定されていない場合、既定で `false` に設定されます。  *アクセサー プロパティ*は、値が取得または設定されるたびにユーザーが指定した関数を呼び出します。  アクセサー プロパティ記述子には、`set` 属性、`get` 属性、またはその両方が含まれます。  詳細については、「[Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)」を参照してください。  
  
## 戻り値  
 指定された内部プロトタイプを持ち、指定されたプロパティ \(存在する場合\) を含む新しいオブジェクトを作成します。  
  
## 例外  
 `TypeError` 例外は、以下のいずれかの条件が当てはまる場合にスローされます。  
  
-   `prototype` 引数がオブジェクトではなく、`null` でもない。  
  
-   `descriptors` 引数の記述子に `value` 属性または `writable` 属性があり、`get` 属性または `set` 属性がある。  
  
-   `descriptors` 引数の記述子に、関数ではない `get` 属性または `set` 属性がある。  
  
## 解説  
 プロトタイプ チェーンを停止するには、この関数で `prototype` パラメーターを `null` にして使用します。  作成されるオブジェクトにはプロトタイプはありません。  
  
## 使用例  
 次の例は `null` プロトタイプを使用してオブジェクトを作成し、列挙可能なプロパティを 2 種類追加します。  
  
```javascript  
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
  
## 使用例  
 次の例は、Object オブジェクトと同じ内部プロトタイプを持つオブジェクトを作成します。  オブジェクト リテラルを使用して作成されたオブジェクトと同じプロトタイプがあることを確認できます。  [Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md) 関数は、元のオブジェクトのプロトタイプを取得します。  オブジェクトのプロパティ記述子を取得するには、[Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md) を使用できます。  
  
```javascript  
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
  
## 使用例  
 次の例は、Shape オブジェクトと同じ内部プロトタイプを持つオブジェクトを作成します。  
  
```javascript  
  
// Create the shape object.  
var Shape = { twoDimensional: true, color: undefined, hasLineSegments: undefined };  
  
var Square = Object.create(Object.getPrototypeOf(Shape));  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 参照  
 [Object.getPrototypeOf 関数](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [isPrototypeOf メソッド \(Object\)](../../javascript/reference/isprototypeof-method-object-javascript.md)   
 [オブジェクトの作成](../../javascript/creating-objects-javascript.md)