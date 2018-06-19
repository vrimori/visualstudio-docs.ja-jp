---
title: Object.defineProperties 関数 (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Object.defineProperties function [JavaScript]
ms.assetid: 2dae6658-a1c9-495f-bf06-bb3e964e6762
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 65f4f5817a105283a26c971bd98869d000ca0bc2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640672"
---
# <a name="objectdefineproperties-function-javascript"></a>Object.defineProperties 関数 (JavaScript)
1 つ以上のプロパティをオブジェクトに追加したり既存のプロパティの属性を変更したります。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.defineProperties(object, descriptors)  
```  
  
## <a name="parameters"></a>パラメーター  
 `object`  
 必須です。 追加またはプロパティを変更する対象となるオブジェクト。 これは、ネイティブ[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]オブジェクトや DOM オブジェクト。  
  
 `descriptors`  
 必須です。 A[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]を 1 つまたは複数の記述子オブジェクトを含むオブジェクト。 各記述子オブジェクトは、データ プロパティまたはアクセサー プロパティについて説明します。  
  
## <a name="return-value"></a>戻り値  
 関数に渡されたオブジェクト。  
  
## <a name="remarks"></a>コメント  
 `descriptors`引数は、1 つまたは複数の記述子オブジェクトを含むオブジェクト。  
  
 A*データ プロパティ*格納したり、値を取得できるプロパティです。 データ プロパティ記述子が含まれています、 `value` 、属性、`writable`属性、またはその両方です。 詳細については、次を参照してください。[データ プロパティとアクセサー プロパティ](../../javascript/advanced/data-properties-and-accessor-properties.md)です。  
  
 *アクセサー プロパティ*プロパティの値を設定または取得するたびに、ユーザー指定の関数を呼び出します。 アクセサー プロパティ記述子には、`set` 属性、`get` 属性、またはその両方が含まれます。  
  
 オブジェクトは、指定した名前を持つプロパティを既に持っている場合は、プロパティの属性が変更されます。 詳細については、次を参照してください。 [Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)です。  
  
 オブジェクトを作成して、新しいオブジェクトにプロパティを追加、使用することができます、 [Object.create 関数](../../javascript/reference/object-create-function-javascript.md)です。  
  
## <a name="adding-properties"></a>プロパティを追加する  
 次の例で、`Object.defineProperties`関数は、ユーザー定義オブジェクトにデータ プロパティとアクセサー プロパティを追加します。  
  
 例では、オブジェクト リテラルを使用して、作成、`descriptors`オブジェクトを`newDataProperty`と`newAccessorProperty`記述子オブジェクト。  
  
```JavaScript  
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
  
 前の例のようには、次の例は、オブジェクト リテラルに動的の代わりにプロパティを追加します。  
  
```JavaScript  
  
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
  
## <a name="modifying-properties"></a>プロパティを変更する  
 オブジェクトのプロパティの属性を変更するには、次のコードを追加します。 `Object.defineProperties`関数を変更、`writable`の属性`newDataProperty`、し、変更、`enumerable`の属性`newAccessorProperty`です。 追加`anotherDataProperty`オブジェクトにプロパティ名が既に存在しないためです。  
  
```  
Object.defineProperties(obj, {  
    newDataProperty: { writable: false },  
    newAccessorProperty: { enumerable: false },  
    anotherDataProperty: { value: "abc" }  
});  
```  
  
## <a name="requirements"></a>要件  
 Internet Explorer 9 標準、Internet Explorer 10 標準でサポートされていると[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]アプリ。 それ以外の場合はサポートされていません DOM オブジェクトに対してのみ、Internet Explorer の 8 でサポートされます。  
  
## <a name="see-also"></a>関連項目  
 [Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames 関数](../../javascript/reference/object-getownpropertynames-function-javascript.md)   
 [Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.create 関数](../../javascript/reference/object-create-function-javascript.md)   
 [Object オブジェクト](../../javascript/reference/object-object-javascript.md)