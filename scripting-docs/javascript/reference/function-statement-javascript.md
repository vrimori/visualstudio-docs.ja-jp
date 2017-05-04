---
title: "function ステートメント (JavaScript) | Microsoft Docs"
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
  - "function_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "宣言 (関数を)"
  - "宣言 (関数を), 構文"
  - "function ステートメント"
  - "new 演算子"
ms.assetid: cc9cfd43-1305-41c8-ad67-545d20f4fafe
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# function ステートメント (JavaScript)
新しい関数を宣言します。  
  
## 構文  
  
```  
function functionname ([arg1 [, arg2 [,...[, argN]]]]) {  
    statements  
}   
```  
  
## パラメーター  
 `functionname`  
 必須です。  関数の名前。  
  
 `arg1...argN`  
 省略可能です。  関数が解釈できる引数をコンマで区切ったリストを指定します。  
  
 `statements`  
 省略可能です。  1 つ以上の [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] ステートメントを指定します。  
  
## 解説  
 `function` ステートメントを使用して、今後使用するための関数を宣言します。  `statements` に記述するコードは、スクリプトの他の場所でこの関数が呼び出されるまで実行されません。  
  
 [return](../../javascript/reference/return-statement-javascript.md) ステートメントは、関数から値を返すために使用します。  `return` ステートメントは必ずしも必要ではありません。関数の終わりに達すると、プログラムは関数から戻ります。  関数で `return` ステートメントが実行されない場合、または `return` ステートメントに式がない場合、関数は `undefined` 値を返します。  
  
> [!NOTE]
>  関数を呼び出すときは、必須の引数とかっこを記述してください。  かっこがない関数を呼び出すと、関数の結果ではなく、関数への参照が返されます。  
  
## 使用例  
 `function` ステートメントの使用例を次に示します。  
  
```javascript  
function myfunction (arg1, arg2) {  
    var r = arg1 * arg2;  
    return(r);  
}  
```  
  
## 使用例  
 関数は、変数に割り当てることができます。  この例を次に示します。  
  
```javascript  
function AddFive(x) {  
    return x + 5;  
}  
  
function AddTen(x) {  
    return x + 10;  
}  
  
var condition = false;  
  
var MyFunc;  
if (condition) {  
    MyFunc = AddFive;  
}  
else {  
    MyFunc = AddTen;  
}  
  
var result = MyFunc(123);  
// Output: 133  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [new 演算子](../../javascript/reference/new-operator-decrementjavascript.md)