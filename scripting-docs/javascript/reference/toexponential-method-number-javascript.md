---
title: "toExponential メソッド (Number) (JavaScript) | Microsoft Docs"
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
  - "toExponential"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toExponential メソッド"
ms.assetid: 7c4a6d84-3c1f-4cc4-a67d-7753e5d4ed66
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toExponential メソッド (Number) (JavaScript)
指数表記の数値を表します。  
  
## 構文  
  
```  
  
numObj. toExponential([fractionDigits])  
```  
  
## パラメーター  
 `numObj`  
 必須です。  **Number** オブジェクトを指定します。  
  
 `fractionDigits`  
 省略可能です。  小数点以下の桁数を指定します。  0 ～ 20 の範囲で指定します。  
  
## 戻り値  
 数値を指数表記で表した文字列を返します。  文字列には、1 桁の整数、小数点、および `fractionDigits` で指定した桁数の小数が格納されます。  
  
 `fractionDigits` を指定しない場合、`toExponential` メソッドは数値を一意に表すために必要な桁数のみを返します。  
  
## 使用例  
  
```javascript  
var num = new Number(123);  
var exp = num.toExponential();  
document.write(exp);  
document.write("<br/>");  
  
num = new Number(123.456);  
exp = num.toExponential(5);  
document.write(exp);  
  
// Output:   
// 1.23e+2  
// 1.23456e+2  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **対象**: [Number オブジェクト](../../javascript/reference/number-object-javascript.md)  
  
## 参照  
 [toFixed メソッド \(Number\)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toPrecision メソッド \(Number\)](../../javascript/reference/toprecision-method-number-javascript.md)