---
title: "if...else ステートメント (JavaScript) | Microsoft Docs"
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
  - "else_JavaScriptKeyword"
  - "if_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "if ステートメント, if...else"
  - "ループ構造, if...else ステートメント"
ms.assetid: dfbe86e8-9c1e-4ef5-bb9c-7d1db7ce2506
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# if...else ステートメント (JavaScript)
式の値に応じて、一連のステートメントを条件付きで実行します。  
  
## 構文  
  
```  
if (condition1) {  
    statement1  
}  
[else if (condition2) {  
    statement2  
}]  
[else {  
    statement3]   
}]  
```  
  
## パラメーター  
 `condition1`  
 必須です。  ブール式を指定します。  `condition1` が `null` または `undefined` の場合、`condition1` は `false` として扱われます。  
  
 `statement1`  
 省略可能です。  `condition1` が **true** の場合に実行するステートメントを指定します。  複合ステートメントを指定することもできます。  
  
 `condition2`  
 評価する条件を指定します。  
  
 `statement2`  
 省略可能です。  `condition2` が `true` の場合に実行するステートメントを指定します。  複合ステートメントを指定することもできます。  
  
 `statement3`  
 `condition1` と `condition2` の両方が `false` の場合、このステートメントが実行されます。  
  
## 使用例  
 `if`、`if else`、および `else` の使用例を次のコードに示します。  
  
 `statement1` と `statement2` を中かっこ \({}\) で囲む習慣を付けておくと、コードが読みやすくなり、不注意によるエラーも減らすことができます。  
  
```javascript  
var z = 3;  
if (x == 5) {  
    z = 10;  
}  
else if (x == 10) {  
    z = 15;  
}  
else {  
    z = 20;  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [条件 \(三項\) 演算子 \(?:\)](../../javascript/reference/conditional-ternary-operator-decrement-javascript.md)