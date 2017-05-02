---
title: "typeof 演算子 (JavaScript) | Microsoft Docs"
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
  - "typeof_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "typeof 演算子"
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# typeof 演算子 (JavaScript)
式のデータ型を識別する文字列を返します。  
  
## 構文  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## 解説  
 *expression* 引数には、型情報を取得する任意の式を指定します。  
  
 `typeof` 演算子は、型情報を文字列で返します。  `typeof` 演算子が返す文字列は、"number"、"string"、"boolean"、"object"、"function"、"undefined" の 6 つです。  
  
 `typeof` の構文のかっこは省略できます。  
  
## 使用例  
 変数のデータ型を調べる例を次に示します。  
  
```javascript  
var index = 5;  
var result = (typeof index === 'number');  
// Output: true  
  
var description = "abc";  
var result = (typeof description === 'string');  
// Output: true  
```  
  
## 使用例  
 宣言されている変数と宣言されていない変数のデータ型が `undefined` かどうかを調べる例を次に示します。  
  
```javascript  
var declared;  
var result = (declared === undefined);  
// Output: true  
  
var result = (typeof declared === 'undefined');  
// Output: true  
  
var result = (typeof notDeclared === 'undefined')  
// Output: true  
  
var obj = {};  
var result = (typeof obj.propNotDeclared === 'undefined');  
// Output: true  
  
// An undeclared variable cannot be used in a comparison without  
// the typeof operator, so the next line generates an error.  
//  var result = (notDeclared === undefined);  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [Array.isArray 関数](../../javascript/reference/array-isarray-function-javascript.md)   
 [Object.getPrototypeOf 関数](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [定数 undefined](../../javascript/reference/undefined-constant-javascript.md)   
 [比較演算子](../../javascript/reference/comparison-operators-javascript.md)   
 [データ型](../../javascript/data-types-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)