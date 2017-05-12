---
title: "String.fromCharCode 関数 (JavaScript) | Microsoft Docs"
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
  - "fromCharCode"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "fromCharCodeAt メソッド"
  - "文字、Unicode から"
ms.assetid: f64120c1-23a7-48ca-8d1c-db3e8856cab4
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# String.fromCharCode 関数 (JavaScript)
多数の Unicode のコード値から 1 つの文字列を返します。  
  
## 構文  
  
```  
String.fromCharCode([code1[, code2[, ...[, codeN]]]])   
```  
  
## パラメーター  
 `String`  
 必須です。  `String` オブジェクトを指定します。  
  
 `code1`, ..., `codeN`  
 省略可能です。  文字列に変換する文字の Unicode でのコード値を指定します。  省略した場合は空の文字列になります。  
  
## 解説  
 この関数は、文字列インスタンスではなく `String` オブジェクトに対して呼び出します。  
  
 このメソッドを使用する方法の例を次に示します。  
  
```javascript  
var test = String.fromCharCode(112, 108, 97, 105, 110);  
document.write(test);  
  
// Output: plain  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## 参照  
 [charCodeAt メソッド \(String\)](../../javascript/reference/charcodeat-method-string-javascript.md)