---
title: "Object.defineProperty 関数 (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- defineProperty function [JavaScript]
- Object.defineProperty function [JavaScript]
ms.assetid: c5d05346-940a-40c2-b12a-e8b25abc8d46
caps.latest.revision: "74"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89291f5c836f74a5dd71099328ce389a12f6fd24
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="objectdefineproperty-function-javascript"></a>Object.defineProperty 関数 (JavaScript)
1 つのプロパティをオブジェクトに追加したり既存のプロパティの属性を変更したります。  
  
## <a name="syntax"></a>構文  
  
```  
Object.defineProperty(object, propertyname, descriptor)  
```  
  
## <a name="parameters"></a>パラメーター  
 `object`  
 必須です。 プロパティを追加または変更するオブジェクトを指定します。 これは、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] のネイティブ オブジェクト (ユーザー定義オブジェクトまたは組み込みオブジェクト) または DOM オブジェクトです。  
  
 `propertyname`  
 必須です。 プロパティ名を含む文字列。  
  
 `descriptor`  
 必須です。 プロパティの記述子を指定します。 これは、データ プロパティまたはアクセサー プロパティ用です。  
  
## <a name="return-value"></a>戻り値  
 変更されたオブジェクト。  
  
## <a name="remarks"></a>コメント  
 `Object.defineProperty` 関数を使用すると、以下の操作を行うことができます。  
  
-   オブジェクトに新しいプロパティを追加します。 オブジェクトにプロパティ名が指定されていない場合に実行されます。  
  
-   既存のプロパティの属性を変更します。 オブジェクトにプロパティ名が既に指定されている場合に実行されます。  
  
 プロパティの定義は、データ プロパティまたはアクセサー プロパティの属性を説明する記述子オブジェクトに含まれます。 記述子オブジェクトは、`Object.defineProperty` 関数のパラメーターです。  
  
 オブジェクトに複数のプロパティを追加する、または既存の複数のプロパティを変更するには、使用できます、 [Object.defineProperties 関数](../../javascript/reference/object-defineproperties-function-javascript.md)です。  
  
## <a name="exceptions"></a>例外  
 `TypeError` 例外は、以下のいずれかの条件が当てはまる場合にスローされます。  
  
-   `object` 引数がオブジェクトではない。  
  
-   オブジェクトは[拡張](../../javascript/reference/object-isextensible-function-javascript.md)し、指定したプロパティ名が存在しません.  
  
-   `descriptor` に `value` 属性または `writable` 属性があり、`get` 属性または `set` 属性がある。  
  
-   `descriptor` に関数ではない、または未定義の `get` 属性または `set` 属性がある。  
  
-   指定されたプロパティ名が既に存在し、既存のプロパティの `configurable` 属性が `false` で、`descriptor` に既存のプロパティとは異なる属性が 1 つ以上ある。 ただし、既存のプロパティの `configurable` 属性が `false` で、`writable` 属性が `true` の場合は、`value` 属性または `writable` 属性が異なってもかまいません。  
  
## <a name="adding-a-data-property"></a>データ プロパティを追加する  
 ユーザー定義オブジェクトにデータ プロパティを追加する `Object.defineProperty` 関数の例を次に示します。 既存の DOM オブジェクトにプロパティを追加する場合は、`var = window.document` の行のコメントを解除します。  
  
```JavaScript  
var newLine = "<br />";  
  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property to the object.  
Object.defineProperty(obj, "newDataProperty", {  
    value: 101,  
    writable: true,  
    enumerable: true,  
    configurable: true  
});  
  
// Set the property value.  
obj.newDataProperty = 102;  
document.write("Property value: " + obj.newDataProperty + newLine);  
  
// Output:  
// Property value: 102  
```  
  
 オブジェクトのプロパティの一覧を表示するには、この例に次のコードを追加します。  
  
```JavaScript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
  
// Output:  
//  newDataProperty: 102  
```  
  
## <a name="modifying-a-data-property"></a>データ プロパティを変更する  
 オブジェクトのプロパティ属性を変更するには、前述の `addDataProperty` 関数に次のコードを追加します。 `descriptor` パラメーターには、`writable` 属性のみがあります。 他のデータ プロパティの属性は同じです。  
  
```JavaScript  
// Modify the writable attribute of the property.  
Object.defineProperty(obj, "newDataProperty", { writable: false });  
  
// List the property attributes by using a descriptor.  
// Get the descriptor with Object.getOwnPropertyDescriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
for (var prop in descriptor) {  
    document.write(prop + ': ' + descriptor[prop]);  
    document.write(newLine);  
}  
  
// Output  
// writable: false  
// value: 102  
// configurable: true  
// enumerable: true  
```  
  
## <a name="adding-an-accessor-property"></a>アクセサー プロパティを追加する  
 ユーザー定義オブジェクトにアクセサー プロパティを追加する `Object.defineProperty` 関数の例を次に示します。  
  
```JavaScript  
var newLine = "<br />";  
  
// Create a user-defined object.  
var obj = {};  
  
// Add an accessor property to the object.  
Object.defineProperty(obj, "newAccessorProperty", {  
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
});  
  
// Set the property value.  
obj.newAccessorProperty = 30;  
document.write("Property value: " + obj.newAccessorProperty + newLine);  
  
// Output:  
// in property set accessor  
// in property get accessor  
// Property value: 30  
  
```  
  
 オブジェクトのプロパティの一覧を表示するには、この例に次のコードを追加します。  
  
```JavaScript  
var names = Object.getOwnPropertyNames(obj);  
for (var i = 0; i < names.length; i++) {  
    var prop = names[i];  
  
    document.write(prop + ': ' + obj[prop]);  
    document.write(newLine);  
}  
// Output:  
// in property get accessor  
// newAccessorProperty: 30  
  
```  
  
## <a name="modifying-an-accessor-property"></a>アクセサー プロパティを変更する  
 オブジェクトのプロパティ属性を変更するには、前述のコードに次のコードを追加します。 `descriptor` パラメーターには、`get` アクセサーの定義のみがあります。 他のプロパティの属性は同じです。  
  
```JavaScript  
// Modify the get accessor.  
Object.defineProperty(obj, "newAccessorProperty", {  
    get: function () { return this.newaccpropvalue; }  
});  
  
// List the property attributes by using a descriptor.  
// Get the descriptor with Object.getOwnPropertyDescriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newAccessorProperty");  
for (var prop in descriptor) {  
    document.write(prop + ': ' + descriptor[prop]);  
    document.write(newLine);  
}  
  
// Output:  
// get: function () { return this.newaccpropvalue; }  
// set: function (x) { document.write("in property set accessor" + newLine); this.newaccpropvalue = x; }  
// configurable: true  
// enumerable: true  
```  
  
## <a name="modifying-a-property-on-a-dom-element"></a>DOM 要素のプロパティを変更する  
 `Object.getOwnPropertyDescriptor` 関数を使用して組み込み DOM プロパティをカスタマイズし、プロパティのプロパティ記述子を取得して変更する方法の例を次に示します。 この例では、ID が "div" の DIV 要素が必要です。  
  
```JavaScript  
// Get the querySelector property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(Element.prototype, "querySelector");  
  
// Make the property read-only.  
descriptor.value = "query";  
descriptor.writable = false;  
// Apply the changes to the Element prototype.  
Object.defineProperty(Element.prototype, "querySelector", descriptor);  
  
// Get a DOM element from the HTML body.  
var elem = document.getElementById("div");  
  
// Attempt to change the value. This causes the revised value attribute to be called.  
elem.querySelector = "anotherQuery";  
document.write(elem.querySelector);  
  
// Output:  
// query  
  
```  
  
## <a name="requirements"></a>要件  
 Internet Explorer 9 標準モードと Internet Explorer 10 標準モードおよび [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリは、すべての機能をサポートします。  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] は DOM オブジェクトをサポートしますが、ユーザー定義オブジェクトはサポートされません。 `enumerable` 属性と `configurable` 属性は、指定できますが使用されません。  
  
## <a name="see-also"></a>関連項目  
 [ドキュメント オブジェクト モデル プロトタイプ、パート 2: アクセサー (get アクセス操作子と set アクセス操作子) のサポート](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Object.defineProperties 関数](../../javascript/reference/object-defineproperties-function-javascript.md)   
 [Object.create 関数](../../javascript/reference/object-create-function-javascript.md)   
 [Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames 関数](../../javascript/reference/object-getownpropertynames-function-javascript.md)