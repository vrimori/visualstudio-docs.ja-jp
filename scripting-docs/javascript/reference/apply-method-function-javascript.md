---
title: "apply メソッド (Function) (JavaScript) | Microsoft Docs"
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
  - "apply"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Apply メソッド"
ms.assetid: b36df78e-b14b-46ca-b5cb-de752d80f40a
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# apply メソッド (Function) (JavaScript)
関数の `this` 値を指定のオブジェクトで置き換え、関数の引数を配列を置き換えて関数を呼び出します。  
  
## 構文  
  
```  
apply([thisObj[,argArray]])  
```  
  
## パラメーター  
 `thisObj`  
 省略可能です。  `this` オブジェクトとして使用するオブジェクトを指定します。  
  
 `argArray`  
 省略可能です。  関数に渡す引数のセットを指定します。  
  
## 解説  
 `argArray` が有効なオブジェクトでない場合、「オブジェクトが必要です」エラーが発生します。  
  
 `argArray` と `thisObj` のどちらも指定しない場合は、元の `this` オブジェクトが `thisObj` として使用され、引数は渡されません。  
  
## 使用例  
 apply メソッドの使用例を次のコードに示します。  
  
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
  
document.write("Function called with apply: <br/>");  
document.write(callMe.apply(3, [ 4, 5 ]));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with apply:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 参照  
 [Function オブジェクト](../../javascript/reference/function-object-javascript.md)