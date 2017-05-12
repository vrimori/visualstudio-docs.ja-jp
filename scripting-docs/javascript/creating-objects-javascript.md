---
title: "オブジェクトの作成 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "コンストラクター関数"
  - "コンストラクター, インクルード (プロパティとメソッドを)"
  - "作成 (オブジェクトを)"
  - "作成 (オブジェクトを), オブジェクトの作成の概要"
  - "作成 (オブジェクトを), コンストラクター関数"
  - "作成 (オブジェクトを), プロトタイプ"
  - "カスタム オブジェクト"
  - "カスタム オブジェクト, 作成"
  - "function コンストラクター"
  - "初期化 (オブジェクトを), コンストラクターの使用"
  - "オブジェクト, 作成 [JavaScript]"
  - "prototype オブジェクト"
ms.assetid: 58d1baa5-4fe8-4a56-a926-5b11765df704
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# オブジェクトの作成 (JavaScript)
いくつかの方法により、JavaScript で独自のオブジェクトを作成できます。  [Object オブジェクト](../javascript/reference/object-object-javascript.md)を直接インスタンス化 して、独自のプロパティとメソッドを追加できます。  または、オブジェクト リテラル表記を使用してオブジェクトを定義できます。  さらに、コンストラクター関数を使用してオブジェクトを定義することもできます。  コンス トラクター関数の使用方法について詳しくは、「[コンストラクターを使用した型の定義](../javascript/advanced/using-constructors-to-define-types.md)」を参照してください。  
  
## 例  
 次のコードは、オブジェクトのインスタンスを作成していくつかのプロパティを追加する方法を示しています。  このケースでは、`pasta` オブジェクトだけに `grain`、`width`、および `shape` プロパティがあります。  
  
```javascript  
var pasta = new Object();  
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
  
## オブジェクト リテラル  
 オブジェクトの 1 つのインスタンスだけを作成するときには、オブジェクト リテラル表記を使用することもできます。  次のコードは、オブジェクト リテラル表記を使用してオブジェクト インスタンスを作成する方法を示しています。  
  
```javascript  
var pasta = {  
    grain: "wheat",  
    width: 0.5,  
    shape: "round"  
};  
```  
  
 また、コンストラクター内のオブジェクト リテラルを使用することもできます。  
  
> [!CAUTION]
>  以下で説明する機能は、[!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] でのみサポートされています。  
  
 [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] では、略式の構文を使用してオブジェクト リテラルを作成できます。  
  
```javascript  
var key = 'a';  
var value = 5;  
  
// Older version  
var obj1 = {  
    key: key,  
    value: value  
};  
  
// Edge mode  
var obj2 = {key, value};  
  
console.log(obj2);  
  
// Output:  
// [object Object] {key: "a", value: 5}  
```  
  
 以下の例では、略式の構文を使用してオブジェクト リテラルにメソッドを定義する方法を示します。  
  
```javascript  
// Older versions  
var obj = {  
    method1: function() {},  
    method2: function() {}  
};  
  
// Edge mode  
var obj = {  
    method1() {},  
    method2() {}  
};  
```  
  
 [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] では、オブジェクト リテラルにプロパティ名を動的に設定することもできます。  次のコード例では、set 構文を動的に使用して、オブジェクトのプロパティ名を作成します。  
  
```javascript  
var propName = "prop_42";  
  
var obj = {  
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
  
```javascript  
var propName = "prop_42";  
  
var obj = {  
    get [propName]() {  
        return 777;  
    }  
}  
  
console.log(obj.prop_42);  
  
// Output:  
// 777  
```  
  
 次のコード例では、、[矢印関数の構文](../javascript/functions-javascript.md)を使用して 42 をプロパティ名に追加することにより、計算済みプロパティを作成します。  
  
```javascript  
var obj = {  
    [ 'prop_' + (() => 42)() ]: 42  
};  
```