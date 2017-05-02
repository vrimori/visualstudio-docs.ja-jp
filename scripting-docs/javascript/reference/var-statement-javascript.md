---
title: "var ステートメント (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/22/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "var_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "宣言 (変数を)、var ステートメント"
  - "var ステートメント"
ms.assetid: 56f900af-a5c4-4667-9664-5956d30f0aae
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# var ステートメント (JavaScript)
変数を宣言します。  
  
## 構文  
  
```  
var variable1 = value1  
```  
  
## Parameters  
 `variable1`  
 宣言される変数の名前を指定します。  
  
 `value1`  
 変数に代入する初期値を指定します。  
  
## 解説  
 変数を宣言するには、`var` ステートメントを使用します。  変数には、スクリプトでそれを宣言するとき、または後で値を代入できます。  
  
 変数は、スクリプトに初めて出現するときに宣言されます。  
  
 `var` キーワードを使用せずに変数を宣言して、それに値を代入することもできます。  これは "暗黙の宣言" であり、望ましくありません。  暗黙の宣言では、変数のスコープがグローバルになります。  プロシージャ レベルで変数を宣言する場合、グローバル スコープとなることは通常望ましくありません。  変数がグローバル スコープになることを回避するには、変数宣言で `var` のキーワードを使用します。  
  
 `var` ステートメントで変数を初期化しない場合は、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 値の `undefined` が自動的に代入されます。  
  
## 使用例  
 次のコードは、`var` ステートメントの使用例です。  
  
```javascript  
var index;  
var name = "Thomas Jefferson";  
var answer = 42, counter, numpages = 10;  
var myarray = new Array();  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [function ステートメント](../../javascript/reference/function-statement-javascript.md)   
 [new 演算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array オブジェクト](../../javascript/reference/array-object-javascript.md)   
 [変数](../../javascript/variables-javascript.md)