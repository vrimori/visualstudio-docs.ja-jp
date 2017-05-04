---
title: "parseFloat 関数 (JavaScript) | Microsoft Docs"
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
  - "parseFloat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "parseFloat メソッド"
ms.assetid: a7d87a69-1919-4623-be85-972e6376dd2d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# parseFloat 関数 (JavaScript)
文字列を浮動小数点数に変換します。  
  
## 構文  
  
```  
parseFloat(numString)   
```  
  
## 解説  
 必須の `numString` 引数は、浮動小数点数値を格納する文字列です。  
  
 `parseFloat` 関数は、引数 `numString` に格納されている数値を返します。  `numString` 引数の先頭に浮動小数点数がない場合は、`NaN` \(Not a Number \(非数値\)\) を返します。  
  
```javascript  
parseFloat("abc")      // Returns NaN.  
parseFloat("1.2abc")   // Returns 1.2.  
```  
  
 値が `NaN` かどうかを調べるには、`isNaN` 関数を使用します。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [Global オブジェクト](../../javascript/reference/global-object-javascript.md)  
  
## 参照  
 [isNaN 関数](../../javascript/reference/isnan-function-javascript.md)   
 [parseInt 関数](../../javascript/reference/parseint-function-javascript.md)   
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)