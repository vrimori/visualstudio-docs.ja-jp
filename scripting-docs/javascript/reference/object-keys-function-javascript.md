---
title: "Object.keys 関数 (JavaScript) | Microsoft Docs"
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
  - "keys メソッド [JavaScript]"
  - "Object.keys メソッド [JavaScript]"
ms.assetid: cf4a7daf-cf28-4467-bc6b-f7f106ec3876
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Object.keys 関数 (JavaScript)
オブジェクトの列挙可能なプロパティおよびメソッドの名前を返します。  
  
## 構文  
  
```javascript  
Object.keys(object)  
```  
  
#### パラメーター  
  
|パラメーター|定義|  
|------------|--------|  
|`object`|必須です。  プロパティとメソッドを含むオブジェクトを指定します。  これには、作成したオブジェクトまたは既存のドキュメント オブジェクト モデル \(DOM\) オブジェクトを使用できます。|  
  
## 戻り値  
 オブジェクトの列挙可能なプロパティとメソッドの名前を含む配列。  
  
## 例外  
 `object` 引数に指定された値がオブジェクトの名前ではない場合、`TypeError` 例外がスローされます。  
  
## 解説  
 `keys` メソッドは、列挙可能なプロパティとメソッドの名前のみを返します。  列挙可能および列挙可能でないプロパティとメソッドの名前を返す場合は、[Object.getOwnPropertyNames 関数](../../javascript/reference/object-getownpropertynames-function-javascript.md) を使用します。  
  
 プロパティの `enumerable` 属性の詳細については、「[Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)」および「[Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)」を参照してください。  
  
## 使用例  
 次の例では、3 種類のプロパティおよびメソッドを持つオブジェクトを作成します。  次に、`keys` メソッドを使用して、オブジェクトのプロパティとメソッドを取得します。  
  
```javascript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
  
    // Define a method.  
    this.toString = function () {  
        return (this.grain + ", " + this.width + ", " + this.shape);  
    }  
}  
  
// Create an object.  
var spaghetti = new Pasta("wheat", 0.2, "circle");  
  
// Put the enumerable properties and methods of the object in an array.  
var arr = Object.keys(spaghetti);  
document.write (arr);  
  
// Output:  
// grain,width,shape,toString  
```  
  
## 使用例  
 Pasta オブジェクトで文字 "g" で始まるすべての列挙可能プロパティの名前を表示する例を次に示します。  
  
```javascript  
// Create a constructor function.  
function Pasta(grain, width, shape) {  
    this.grain = grain;  
    this.width = width;  
    this.shape = shape;  
}  
  
var polenta = new Pasta("corn", 1, "mush");  
  
var keys = Object.keys(polenta).filter(CheckKey);  
document.write(keys);  
  
// Check whether the first character of a string is "g".  
function CheckKey(value) {  
    var firstChar = value.substr(0, 1);  
    if (firstChar.toLowerCase() == "g")  
        return true;  
    else  
        return false;  
}  
  
// Output:  
// grain  
```  
  
## 必要条件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 参照  
 [Object.getOwnPropertyNames 関数](../../javascript/reference/object-getownpropertynames-function-javascript.md)