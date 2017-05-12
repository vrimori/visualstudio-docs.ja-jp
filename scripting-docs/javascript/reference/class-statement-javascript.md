---
title: "class ステートメント (JavaScript) | Microsoft Docs"
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
ms.assetid: bf45ebad-4678-4062-88df-55d32b603c69
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# class ステートメント (JavaScript)
新しいクラスを宣言します。  
  
## 構文  
  
```  
class classname () [extends object] {  
    [constructor([arg1 [,... [,argN]]]) {  
        statements  
    }]  
    [[static] method([arg1 [,... [,argN]]]) {  
        statements  
    }]  
}  
```  
  
#### パラメーター  
 `classname`  
 必須です。  クラスの名前。  
  
 `object`  
 省略可能です。  新しいクラスがプロパティとメソッドを継承するオブジェクトまたはクラス。  
  
 `constructor`  
 省略可能です。  新しいクラスのインスタンスを初期化するコンストラクター関数。  
  
 `arg1...argN`  
 省略可能です。  省略可能な、関数が認識できる引数のコンマ区切りのリスト。  
  
 `statements`  
 省略可能です。  1 つまたは複数の [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ステートメント。  
  
 `static`  
 省略可能です。  静的メソッドを指定します。  
  
 `method`  
 省略可能です。  クラス インスタンスで呼び出すことのできる 1 つまたは複数の [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] インスタンスまたは静的メソッド。  
  
## 解説  
 クラスによって、プロトタイプ ベースの継承、コンストラクター、インスタンス メソッド、および静的メソッドを使用することにより、新しいオブジェクトを作成することができます。  クラス コンストラクターやクラス メソッド内にある `super` オブジェクトを使用して、親クラスや親オブジェクト内にある同じコンストラクターやメソッドを呼び出すことができます。  必要に応じて、クラス名の後に `extends` ステートメントを使用して、新しいクラスがメソッドを継承するクラスやオブジェクトを指定できます。  
  
## 使用例  
  
```javascript  
class Spelunking extends EXPERIENCE.Outdoor {  
  constructor(name, location) {  
    super(name, location);  
  
    this.minSkill = Spelunking.defaultSkill();  
    //...  
  }  
  update(minSkill) {  
    //...  
    super.update(minSkill);  
  }  
  static defaultSkill() {  
    return new EXPERIENCE.Level3();  
  }  
}  
```  
  
## 使用例  
 クラスのために計算されたプロパティ名を作成することもできます。  次のコード例では、`set` 構文を使用して、計算されたプロパティ名を作成します。  
  
```javascript  
var propName = "prop_42";  
  
class Spelunking {  
    set [propName](v) {  
        this.value = v;  
    }  
};  
  
var s = new Spelunking();  
console.log(s.value);  
s.prop_42 = 42;  
console.log(s.value);  
  
// Output:  
// undefined  
// 42  
  
```  
  
## 使用例  
 次のコード例では、`get` 構文を使用して、クラスのために計算されたプロパティ名を動的に作成します。  
  
```javascript  
var propName = "prop_42";  
  
class Spelunking {  
    get [propName]() {  
        return 777;  
    }  
}  
  
var s = new Spelunking();  
console.log(s.prop_42);  
  
// Output:  
// 777  
```  
  
## 必要条件  
 [!INCLUDE[jsv12exp](../../javascript/reference/includes/jsv12exp-md.md)]