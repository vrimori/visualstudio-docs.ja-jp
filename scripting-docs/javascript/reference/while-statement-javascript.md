---
title: "while ステートメント (JavaScript) | Microsoft Docs"
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
  - "while_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ループ構造、while ステートメント"
  - "while ステートメント"
ms.assetid: d63777cf-0e1a-4555-8d3a-334381001f48
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# while ステートメント (JavaScript)
指定された条件が `false` になるまで \(一連の\) ステートメントを実行します。  
  
## 構文  
  
```  
while (expression) {  
    statements  
}   
```  
  
## Parameters  
 `expression`  
 Required.  ループの各反復処理の前にチェックするブール式を指定します。  `expression` が `true` の場合、ループが実行されます。  If `expression` is `false`, the loop is terminated.  
  
 `statements`  
 Optional.  `expression` が `true` の場合に実行する 1 つ以上のステートメントを指定します。  
  
## 解説  
 `while` ステートメントでは、ループが初めて実行される前に `expression` がチェックされます。  この時点で `expression` が `false` の場合、ループは一度も実行されません。  
  
## 使用例  
 次のコードは、`while` ステートメントの使用例です。  
  
```javascript  
var i = 0;  
var j = 10;  
while (i < 100) {  
    if (i == j)  
        break;  
    i++;  
}  
document.write(i);  
  
// Output: 10  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [break ステートメント](../../javascript/reference/break-statement-javascript.md)   
 [continue ステートメント](../../javascript/reference/continue-statement-javascript.md)   
 [do...while ステートメント](../../javascript/reference/do-dot-dot-dot-while-statement-javascript.md)   
 [for ステートメント](../../javascript/reference/for-statement-javascript.md)   
 [for...in ステートメント](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)