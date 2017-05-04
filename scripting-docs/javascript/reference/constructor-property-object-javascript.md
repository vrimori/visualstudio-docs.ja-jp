---
title: "constructor プロパティ (Object) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "constructor"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "constructor プロパティ"
ms.assetid: 6f5d0e9d-e85f-4fde-b558-744510483d69
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# constructor プロパティ (Object) (JavaScript)
オブジェクトを作成する関数を指定します。  
  
## 構文  
  
```  
  
object.constructor  
```  
  
## 解説  
 必須の `object` オブジェクトには、オブジェクトまたは関数の名前を指定します。  
  
 `constructor` プロパティは、プロトタイプを持つあらゆるオブジェクトのプロトタイプのメンバーです。  これには、`Global` オブジェクトと `Math` オブジェクトを除くすべての組み込み [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] オブジェクトが含まれています。  `constructor` プロパティには、特定のオブジェクトのインスタンスを作成する関数への参照が格納されます。  
  
## 使用例  
 constructor プロパティの使用例を次に示します。  
  
```javascript  
// A constructor function.  
function MyObj() {  
    this.number = 1;  
}  
  
var x = new String("Hi");  
  
if (x.constructor == String)  
    document.write("Object is a String.");  
document.write ("<br />");  
  
var y = new MyObj;  
if (y.constructor == MyObj)  
    document.write("Object constructor is MyObj.");  
  
// Output:  
// Object is a String.  
// Object constructor is MyObj.  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 参照  
 [prototype プロパティ \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)