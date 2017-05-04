---
title: "コンストラクターを使用した型の定義 | Microsoft Docs"
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
  - "コンストラクター, 作成"
  - "作成 (オブジェクトを), コンストラクター関数"
  - "関数, コンストラクター関数"
  - "オブジェクト, 作成 [JavaScript]"
ms.assetid: e869702e-4caf-4513-8dd5-fe690535f8aa
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# コンストラクターを使用した型の定義
コンストラクターは、[Object](../../javascript/objects-and-arrays-javascript.md) の特定の型のインスタンスを作成する関数です。  コンストラクターは、**new** キーワードを使用して呼び出します。  JavaScript の組み込みオブジェクトとカスタム オブジェクトのコンストラクターの例をいくつか次に示します。  
  
## コンストラクターの例  
  
```javascript  
// Creates a generic object.  
var myObject = new Object();  
// Creates a Date object.  
var myBirthday = new Date(1961, 5, 10);  
// Creates a user defined object.  
var myCar = new Car();  
```  
  
 コンストラクター関数には、新しく作成された空のオブジェクトへの参照である **this** キーワードが含まれます。  コンストラクターは、プロパティを作成し、初期値を設定することによって、新しいオブジェクトを初期化します。  コンストラクターは、構築したオブジェクトへの参照を戻します。  
  
## コンストラクターの記述  
 オブジェクトは、**new** 演算子および **Object\(\)**、**Date\(\)**、および **Function\(\)** などの定義済みコンストラクター関数を使用して作成できます。  一連のプロパティとメソッドを定義するカスタム コンストラクター関数を作成することもできます。  カスタム コンストラクターの例を次に示します。  
  
```javascript  
function Circle (xPoint, yPoint, radius) {  
    this.x = xPoint;  // The x component of the center of the circle.  
    this.y = yPoint;  // The y component of the center of the circle.  
    this.r = radius;  // The radius of the circle.  
}  
```  
  
 Circle コンストラクターを呼び出すときは、円の中心点と半径の値を指定します。  3 つのプロパティを含む Circle オブジェクトが作成されます。  Circle オブジェクトのインスタンスを作成するコードは次のとおりです。  
  
```javascript  
var aCircle = new Circle(5, 11, 99);  
```  
  
 カスタム コンストラクターで作成されるオブジェクトは、すべて `object` 型です。  JavaScript には、`object`、`function`、`string`、`number`、`boolean`、`undefined` の 6 つの型しかありません。  詳細については、「[typeof 演算子](../../javascript/reference/typeof-operator-decrementjavascript.md)」を参照してください。  
  
## 参照  
 [bind メソッドの使用](../../javascript/advanced/using-the-bind-method-javascript.md)