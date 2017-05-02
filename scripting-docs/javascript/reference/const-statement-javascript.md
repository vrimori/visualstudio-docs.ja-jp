---
title: "const ステートメント (JavaScript) | Microsoft Docs"
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
  - "const_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "宣言 (変数を)、const ステートメント"
  - "const ステートメント"
ms.assetid: 3ad0840f-437f-4163-9571-86ecc5ddb987
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# const ステートメント (JavaScript)
定数値を含むブロック スコープ変数を宣言します。  
  
## 構文  
  
```  
const constant1 = value1  
```  
  
#### パラメーター  
 `constant1`  
 宣言される変数の名前を指定します。  
  
 `value1`  
 変数に代入する初期値を指定します。  
  
## 解説  
 `const` ステートメントを使用して、スコープが宣言されたブロックに制限されている、定数値を含む変数を宣言します。  この変数の値は変更できません。  
  
 `const` を使用して宣言された変数は、宣言時に初期化される必要があります。  
  
## 使用例  
 次の例は、`const` ステートメントの使用方法を示します。  
  
```javascript  
var c = 10;  
{  
    const c = 2;  
   // At this point, c = 2.  
}  
// At this point, c = 10.  
  
// Additional ways to declare a variable using const.  
const name = "Thomas Jefferson";  
const answer = 42, numpages = 10;  
const myarray = new Array();  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## 参照  
 [let ステートメント](../../javascript/reference/let-statement-javascript.md)   
 [new 演算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array オブジェクト](../../javascript/reference/array-object-javascript.md)   
 [変数](../../javascript/variables-javascript.md)