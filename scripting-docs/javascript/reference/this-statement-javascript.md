---
title: "this ステートメント (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "this_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "コンストラクター, 参照 (現在のオブジェクトを)"
  - "this ステートメント"
ms.assetid: 8510a00b-2f14-4700-a276-4d9a523c5112
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# this ステートメント (JavaScript)
現在のオブジェクトを返します。  
  
## 構文  
  
```  
this.property  
```  
  
## 解説  
 必須の `property` 引数は、現在のオブジェクトのいずれかのプロパティです。  
  
 キーワード `this` は、オブジェクト コンストラクターで現在のオブジェクトを参照するために使用できます。  
  
## 使用例  
 次のコードは、**this** ステートメントを使って新しく作成された Car オブジェクトを示している例です。このコードでは、3 つのプロパティに値を代入しています。  
  
```javascript  
function Car(color, make, model){  
   this.color = color;  
   this.make = make;  
   this.model = model;  
}  
```  
  
 通常、キーワード **this** は、他のオブジェクトのスコープ外で使用された場合に **window** オブジェクトを示します。  ただし、イベント ハンドラー内では、`this` はイベントを発生させた DOM 要素を示します。  
  
 \(Internet Explorer 9 以降用の\) 次のコードでは、イベント ハンドラーは、ID が "clicker" のボタンの文字列バージョンを出力します。  
  
```javascript  
document.getElementById("clicker").addEventListener("click", eventHandler, false);  
  
        function eventHandler(ev) {  
            document.write(this.toString());  
        }  
  
// Output (when you click the button): [object HTMLButtonElement]  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [new 演算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [bind メソッドの使用](../../javascript/advanced/using-the-bind-method-javascript.md)