---
title: コンストラクターを使用した型の定義 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- creating objects, constructor functions
- constructor functions
- functions, constructor functions
- objects, creating [JavaScript]
- constructors, creating
ms.assetid: e869702e-4caf-4513-8dd5-fe690535f8aa
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0bff42606fda27e00a537cc227a0b636e016f7c6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24569182"
---
# <a name="using-constructors-to-define-types"></a>コンストラクターを使用した型の定義
コンストラクターは、[Object](../../javascript/objects-and-arrays-javascript.md) の特定の型のインスタンスを作成する関数です。 コンストラクターは、**new** キーワードを使って呼び出します。 JavaScript の組み込みオブジェクトとカスタム オブジェクトのコンストラクターの例をいくつか次に示します。  
  
## <a name="constructor-examples"></a>コンストラクターの例  
  
```JavaScript  
// Creates a generic object.  
var myObject = new Object();  
// Creates a Date object.  
var myBirthday = new Date(1961, 5, 10);  
// Creates a user defined object.  
var myCar = new Car();  
```  
  
 コンストラクター関数には、新しく作成された空のオブジェクトへの参照である **this** キーワードが含まれます。 コンストラクターは、プロパティを作成し、初期値を設定することによって、新しいオブジェクトを初期化します。 コンストラクターは、構築したオブジェクトへの参照を戻します。  
  
## <a name="writing-constructors"></a>コンストラクターの記述  
 オブジェクトは、**new** 演算子と **Object()**、**Date()**、**Function()** などの定義済みコンストラクター関数を組み合わせて使って作成できます。 一連のプロパティとメソッドを定義するカスタム コンストラクター関数を作成することもできます。 カスタム コンストラクターの例を次に示します。  
  
```JavaScript  
function Circle (xPoint, yPoint, radius) {  
    this.x = xPoint;  // The x component of the center of the circle.  
    this.y = yPoint;  // The y component of the center of the circle.  
    this.r = radius;  // The radius of the circle.  
}  
```  
  
 Circle コンストラクターを呼び出すときは、円の中心点と半径の値を指定します。 3 つのプロパティを含む Circle オブジェクトが作成されます。 Circle オブジェクトのインスタンスを作成するコードは次のとおりです。  
  
```JavaScript  
var aCircle = new Circle(5, 11, 99);  
```  
  
 カスタム コンストラクターで作成されるオブジェクトは、すべて `object` 型です。 JavaScript には、`object`、`function`、`string`、`number`、`boolean`、`undefined` の 6 つの型しかありません。 詳しくは、「[typeof 演算子](../../javascript/reference/typeof-operator-decrementjavascript.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目  
 [bind メソッドの使用](../../javascript/advanced/using-the-bind-method-javascript.md)