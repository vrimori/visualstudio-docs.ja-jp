---
title: "do...while ステートメント (JavaScript) | Microsoft Docs"
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
  - "do_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "do...while ステートメント"
  - "終了 (ループを)"
  - "ループ構造、do と do-while"
ms.assetid: 8b7782ba-fbad-48cd-9639-193566da6ae5
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# do...while ステートメント (JavaScript)
ステートメント ブロックを一度実行し、その後、条件式の評価が `false` になるまでループ実行を繰り返します。  
  
## 構文  
  
```  
do {  
    statement  
}  
while (expression) ;   
```  
  
## Parameters  
 `statement`  
 Required.  `expression` が `true` の場合に実行するステートメントを指定します。  複合ステートメントを指定することもできます。  
  
 `expression`  
 Required.  `true` または `false` のブール値に強制変換できる式を指定します。  `expression` が `true` の場合、ループが再び実行されます。  `expression` が `false` の場合、ループ処理は終了します。  
  
## 解説  
 `while` ステートメントとは異なり、`do...while` ループは条件式が評価される前に 1 回実行されます。  
  
 `do…while` ブロック内の任意の行で、`break` ステートメントを使用してループから抜けることができます。同様に、任意の行で `continue` ステートメントを使用して、`while` 式に直接移ることができます。  
  
## 使用例  
 次の例では、変数 `i` が 10 未満である限り、`do...while` ループ内のステートメントが実行されます。  
  
```javascript  
var i = 0;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 0 1 2 3 4 5 6 7 8 9   
```  
  
## 使用例  
 次の例では、条件が満たされない場合でもループ内のステートメントが 1 回実行されます。  
  
```javascript  
var i = 10;  
do {  
    document.write(i + " ");  
    i++;  
} while (i < 10);  
  
// Output: 10  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 参照  
 [break ステートメント](../../javascript/reference/break-statement-javascript.md)   
 [continue ステートメント](../../javascript/reference/continue-statement-javascript.md)   
 [for ステートメント](../../javascript/reference/for-statement-javascript.md)   
 [for...in ステートメント](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [while ステートメント](../../javascript/reference/while-statement-javascript.md)   
 [ラベル付きステートメント](../../javascript/reference/labeled-statement-javascript.md)