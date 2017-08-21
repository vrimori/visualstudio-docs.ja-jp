---
title: "オブジェクトの作成 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- constructors, including properties and methods
- function constructor
- creating objects, constructor functions
- constructor functions
- prototype objects
- creating objects
- custom objects, creating
- creating objects, about creating objects
- objects, creating [JavaScript]
- creating objects, prototypes
- custom objects
- initializing objects, using constructors
ms.assetid: 58d1baa5-4fe8-4a56-a926-5b11765df704
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 359e1eb5df8f19774d352ace631802367b6dd8c9
ms.openlocfilehash: 0ba7962179cc2f0fcb972caee692edabee368c7d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/11/2017

---
# <a name="creating-objects-javascript"></a>オブジェクトの作成 (JavaScript)
いくつかの方法により、JavaScript で独自のオブジェクトを作成できます。 [Object オブジェクト](../javascript/reference/object-object-javascript.md)を直接インスタンス化して、独自のプロパティとメソッドを追加できます。 または、オブジェクト リテラル表記を使用してオブジェクトを定義できます。 さらに、コンストラクター関数を使用してオブジェクトを定義することもできます。 コンストラクター関数の使用方法について詳しくは、「[Using Constructors to Define Types](../javascript/advanced/using-constructors-to-define-types.md)」(コンストラクターを使用して型を定義する) を参照してください。  
  
## <a name="example"></a>例  
 次のコードは、オブジェクトのインスタンスを作成していくつかのプロパティを追加する方法を示しています。 このケースでは、`pasta` オブジェクトだけに `grain`、`width`、および `shape` プロパティがあります。  
  
```JavaScript  
const pasta = new Object();  
pasta.grain = "wheat";  
pasta.width = 0.5;  
pasta.shape = "round";  
pasta.getShape = function() {   
    return this.shape;   
};  
document.write(pasta.grain);  
document.write("<br/>");  
document.write(pasta.getShape());  
  
// Output:  
// wheat  
// round  
  
```  
  
## <a name="object-literals"></a>オブジェクト リテラル  
 オブジェクトの 1 つのインスタンスだけを作成するときには、オブジェクト リテラル表記を使用することもできます。 次のコードは、オブジェクト リテラル表記を使用してオブジェクト インスタンスを作成する方法を示しています。  
  
```JavaScript  
const pasta = {  
    grain: "wheat",  
    width: 0.5,  
    shape: "round"  
};  
```  
  
 また、コンストラクター内のオブジェクト リテラルを使用することもできます。  
  
> [!CAUTION]
>  以下で説明する機能は、[!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] でのみサポートされています。  
  
 [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] では、略式の構文を使用してオブジェクト リテラルを作成できます。  
  
```JavaScript  
const key = 'a';  
const value = 5;  
  
// Older version  
const obj1 = {  
    key: key,  
    value: value  
};  
  
// Edge mode  
const obj2 = {key, value};  
  
console.log(obj2);  
  
// Output:  
// [object Object] {key: "a", value: 5}  
```  
  
 以下の例では、略式の構文を使用してオブジェクト リテラルにメソッドを定義する方法を示します。  
  
```JavaScript  
// Older versions  
const obj = {  
    method1: function() {},  
    method2: function() {}  
};  
  
// Edge mode  
const obj = {  
    method1() {},  
    method2() {}  
};  
```  
  
 [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] では、オブジェクト リテラルにプロパティ名を動的に設定することもできます。 次のコード例では、set 構文を動的に使用して、オブジェクトのプロパティ名を作成します。  
  
```JavaScript  
const propName = "prop_42";  
  
const obj = {  
    value: 0,  
    set [propName](v) {  
        this.value = v;  
    }  
}  
  
console.log(obj.value);  
// Runs the setter property.  
obj.prop_42 = 777;  
console.log(obj.value);  
  
// Output:  
// 0  
// 777  
  
```  
  
 次のコード例では、get 構文を動的に使用して、オブジェクトのプロパティ名を作成します。  
  
```JavaScript  
const propName = "prop_42";  
  
const obj = {  
    get [propName]() {  
        return 777;  
    }  
}  
  
console.log(obj.prop_42);  
  
// Output:  
// 777  
```  
  
 次のコード例では、[矢印関数の構文](../javascript/functions-javascript.md)を使用して 42 をプロパティ名に追加することにより、計算済みプロパティを作成します。  
  
```JavaScript  
const obj = {  
    [ 'prop_' + (() => 42)() ]: 42  
};  
```

