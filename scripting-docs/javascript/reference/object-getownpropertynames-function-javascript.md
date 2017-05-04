---
title: "Object.getOwnPropertyNames 関数 (JavaScript) | Microsoft Docs"
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
  - "getOwnPropertyNames メソッド [JavaScript]"
  - "Object.getOwnPropertyNames メソッド [JavaScript]"
ms.assetid: 59f4b6b1-02be-44b3-a06c-a5ca8f70c3d8
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Object.getOwnPropertyNames 関数 (JavaScript)
オブジェクト独自のプロパティの名前を返します。  オブジェクト独自のプロパティとは、そのオブジェクトで直接定義され、オブジェクトのプロトタイプから継承されないプロパティです。  オブジェクトのプロパティには、フィールド \(オブジェクト\) と関数の両方が含まれます。  
  
## 構文  
  
```javascript  
Object.getOwnPropertyNames(object)  
```  
  
#### パラメーター  
  
|パラメーター|定義|  
|------------|--------|  
|`object`|必須です。  独自のプロパティを格納するオブジェクトを指定します。|  
  
## 戻り値  
 オブジェクト独自のプロパティの名前を含む配列を指定します。  
  
## 例外  
 `object` 引数に指定された値がオブジェクトの名前ではない場合、`TypeError` 例外がスローされます。  
  
## 解説  
 `getOwnPropertyNames` メソッドは、列挙可能および列挙可能でないプロパティとメソッドの名前を返します。  列挙可能なプロパティとメソッドの名前のみを返すには、[Object.keys 関数](../../javascript/reference/object-keys-function-javascript.md) メソッドを使用します。  
  
## 使用例  
 次の例では、3 種類のプロパティおよびメソッドを持つオブジェクトを作成します。  その後、`getOwnPropertyNames` メソッドを使用して、オブジェクト独自のプロパティ \(メソッドを含む\) を取得します。  
  
```javascript  
function Pasta(grain, width, shape) {  
    // Define properties.  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Get the own property names.  
var arr = Object.getOwnPropertyNames(spaghetti);  
document.write (arr);  
  
// Output:  
//   grain,width,shape,toString  
```  
  
## 使用例  
 Pasta コンストラクターで作成した spaghetti オブジェクトの文字 "s" で始まるプロパティの名前を表示する例を次に示します。  
  
```javascript  
function Pasta(grain, size, shape) {  
    this.grain = grain;   
    this.size = size;   
    this.shape = shape;   
}  
  
var spaghetti = new Pasta("wheat", 2, "circle");  
  
var names = Object.getOwnPropertyNames(spaghetti).filter(CheckKey);  
document.write(names);   
  
// Check whether the first character of a string is 's'.   
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);   
    if (firstChar.toLowerCase() == 's')  
        return true;   
    else  
         return false;   
}  
// Output:  
// size,shape  
```  
  
## 必要条件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 参照  
 [Object.keys 関数](../../javascript/reference/object-keys-function-javascript.md)