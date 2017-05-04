---
title: "call メソッド (Function) (JavaScript) | Microsoft Docs"
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
  - "call"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "call メソッド"
ms.assetid: fa356dec-48e6-4f75-8bf3-c1814a76818f
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# call メソッド (Function) (JavaScript)
現在のオブジェクトの代わりに、他のオブジェクトを使用してメソッドを呼び出します。  
  
## 構文  
  
```  
call([thisObj[, arg1[, arg2[,  [, argN]]]]])  
```  
  
## パラメーター  
 `thisObj`  
 省略可能です。  現在のオブジェクトとして使用するオブジェクトを指定します。  
  
 `arg1, arg2, , argN`  
 省略可能です。  メソッドに渡す引数のリストです。  
  
## 解説  
 別のオブジェクトに代わってメソッドを呼び出すときに `call` メソッドを使用します。  このメソッドを使用すると、関数の `this` オブジェクトを元のコンテキストから `thisObj` で指定した新しいオブジェクトに変更できます。  
  
 `thisObj` を指定しない場合は、`global` オブジェクトが `thisObj` として使用されます。  
  
## 使用例  
 `call` メソッドの使用例を次のコードに示します。  
  
```javascript  
function callMe(arg1, arg2){  
    var s = "";  
  
    s += "this value: " + this;  
    s += "<br />";  
    for (i in callMe.arguments) {  
        s += "arguments: " + callMe.arguments[i];  
        s += "<br />";  
    }  
    return s;  
}  
  
document.write("Original function: <br/>");  
document.write(callMe(1, 2));  
document.write("<br/>");  
  
document.write("Function called with call: <br/>");  
document.write(callMe.call(3, 4, 5));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with call:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 参照  
 [Function オブジェクト](../../javascript/reference/function-object-javascript.md)   
 [apply メソッド \(Function\)](../../javascript/reference/apply-method-function-javascript.md)