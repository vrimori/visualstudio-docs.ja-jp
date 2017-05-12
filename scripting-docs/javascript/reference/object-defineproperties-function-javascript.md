---
title: "Object.defineProperties 関数 (JavaScript) | Microsoft Docs"
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
  - "Object.defineProperties 関数 [JavaScript]"
ms.assetid: 2dae6658-a1c9-495f-bf06-bb3e964e6762
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Object.defineProperties 関数 (JavaScript)
1 つ以上のプロパティをオブジェクトに追加したり既存のプロパティの属性を変更したります。  
  
## 構文  
  
```  
  
object.defineProperties(object, descriptors)  
```  
  
## Parameters  
 `object`  
 Required.  プロパティを追加または変更するオブジェクトを指定します。  これは [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のネイティブ オブジェクトまたは DOM オブジェクトです。  
  
 `descriptors`  
 Required.  1 つ以上の記述子オブジェクトを含む [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] オブジェクトを指定します。  各記述子オブジェクトは、データ プロパティまたはアクセサー プロパティについて記述します。  
  
## 戻り値  
 関数に渡されたオブジェクト。  
  
## 解説  
 `descriptors` 引数は、1 つ以上の記述子オブジェクトを含むオブジェクトです。  
  
 *データ プロパティ*は、値を格納および取得できるプロパティです。  データ プロパティ記述子には、`value` 属性、`writable` 属性、またはその両方が含まれます。  詳細については、「[データ プロパティとアクセサー プロパティ](../../javascript/advanced/data-properties-and-accessor-properties.md)」を参照してください。  
  
 *アクセサー プロパティ*は、プロパティ値が設定または取得されるたびにユーザーが指定した関数を呼び出します。  アクセサー プロパティ記述子には、`set` 属性、`get` 属性、またはその両方が含まれます。  
  
 オブジェクトに既に指定された名前のプロパティがある場合は、プロパティの属性が変更されます。  詳細については、「[Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)」を参照してください。  
  
 オブジェクトを作成し、新しいオブジェクトにプロパティを追加するには、[Object.create 関数](../../javascript/reference/object-create-function-javascript.md) を使用できます。  
  
## プロパティの追加  
 ユーザー定義オブジェクトにデータ プロパティとアクセサー プロパティを追加する `Object.defineProperties` 関数の例を次に示します。  
  
 例では、オブジェクト リテラルを使用して、`newDataProperty` 記述子オブジェクトと `newAccessorProperty` 記述子オブジェクトを含む `descriptors` オブジェクトを作成します。  
  
```javascript  
var newLine = "<br />";  
  
var obj = {};  
Object.defineProperties(obj, {  
    newDataProperty: {  
        value: 101,  
        writable: true,  
        enumerable: true,  
        configurable: true  
    },  
    newAccessorProperty: {  
        set: function (x) {  
            document.write("in property set accessor" + newLine);  
            this.newaccpropvalue = x;  
        },  
        get: function () {  
            document.write("in property get accessor" + newLine);  
            return this.newaccpropvalue;  
        },  
        enumerable: true,  
        configurable: true  
    }});  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
 前の例のように、次の例は、オブジェクトのリテラルではなくプロパティを動的に追加します。  
  
```javascript  
  
var newLine = "<br />";  
  
// Create the descriptors object.  
var descriptors = new Object();  
  
// Add a data property descriptor to the descriptors object.  
descriptors.newDataProperty = new Object();  
descriptors.newDataProperty.value = 101;  
descriptors.newDataProperty.writable = true;  
descriptors.newDataProperty.enumerable = true;  
descriptors.newDataProperty.configurable = true;  
  
// Add an accessor property descriptor to the descriptors object.  
descriptors.newAccessorProperty = new Object();  
descriptors.newAccessorProperty.set = function (x) {  
    document.write("in property set accessor" + newLine);  
    this.newaccpropvalue = x;  
};  
descriptors.newAccessorProperty.get = function () {  
    document.write("in property get accessor" + newLine);  
    return this.newaccpropvalue;  
};  
descriptors.newAccessorProperty.enumerable = true;  
descriptors.newAccessorProperty.configurable = true;  
  
// Call the Object.defineProperties function.  
var obj = new Object();  
Object.defineProperties(obj, descriptors);  
  
// Set the accessor property value.  
obj.newAccessorProperty = 10;  
document.write ("newAccessorProperty value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// newAccessorProperty value: 10  
  
```  
  
## プロパティの変更  
 オブジェクトのプロパティ属性を変更するには、次のコードを追加します。  `Object.defineProperties` 関数は、`newDataProperty` の `writable` の属性を変更し、`newAccessorProperty` の `enumerable` の属性を変更します。  オブジェクトにプロパティ名 `anotherDataProperty` が存在しないので、それをオブジェクトに追加します。  
  
```  
Object.defineProperties(obj, {  
    newDataProperty: { writable: false },  
    newAccessorProperty: { enumerable: false },  
    anotherDataProperty: { value: "abc" }  
});  
```  
  
## 必要条件  
 Internet Explorer 9 標準モード、Internet Explorer 10 標準モード、および [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリでサポートされています。  Internet Explorer 8 では、DOM オブジェクトのみサポートされていますが、それ以外はサポートされていません。  
  
## 参照  
 [Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames 関数](../../javascript/reference/object-getownpropertynames-function-javascript.md)   
 [Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.create 関数](../../javascript/reference/object-create-function-javascript.md)   
 [Object オブジェクト](../../javascript/reference/object-object-javascript.md)