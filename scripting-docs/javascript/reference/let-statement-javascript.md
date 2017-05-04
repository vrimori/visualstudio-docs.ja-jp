---
title: "let ステートメント (JavaScript) | Microsoft Docs"
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
  - "let_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "let ステートメント"
  - "宣言 (変数を)、let ステートメント"
ms.assetid: c7e4f8a9-8f54-47b6-aed2-956959c1ecfd
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# let ステートメント (JavaScript)
ブロック スコープ変数を宣言します。  
  
## 構文  
  
```  
let variable1 = value1  
```  
  
#### パラメーター  
 `variable1`  
 宣言される変数の名前を指定します。  
  
 `value1`  
 変数に代入する初期値を指定します。  
  
## 解説  
 `let` ステートメントを使用して、スコープが宣言されたブロックに制限されている、変数を宣言します。  変数には、スクリプトでそれを宣言するとき、または後で値を代入できます。  
  
 `let` を使用して宣言された変数は、宣言の前に使用するとエラーになります。  
  
 `let` ステートメントで変数を初期化しない場合は、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 値の `undefined` が自動的に代入されます。  
  
## 使用例  
 次の例は、`let` ステートメントの使用方法を示します。  
  
```javascript  
var  l = 10;  
{  
    let l = 2;  
   // At this point, l = 2.  
}  
// At this point, l = 10.  
  
// Additional ways to declare a variable using let.  
let index;  
let name = "Thomas Jefferson";  
let answer = 42, counter, numpages = 10;  
let myarray = new Array();  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 参照  
 [const ステートメント](../../javascript/reference/const-statement-javascript.md)   
 [new 演算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array オブジェクト](../../javascript/reference/array-object-javascript.md)   
 [変数](../../javascript/variables-javascript.md)