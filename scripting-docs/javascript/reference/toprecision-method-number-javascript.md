---
title: "toPrecision メソッド (Number) (JavaScript) | Microsoft Docs"
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
  - "toPrecision"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toPrecision メソッド"
ms.assetid: ac13c82f-1038-447a-823f-f755bba535ca
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toPrecision メソッド (Number) (JavaScript)
指定された桁数の指数表記または固定小数点表記の数値を文字列で表します。  
  
## 構文  
  
```  
  
numObj.toPrecision([precision])  
```  
  
## パラメーター  
 `numObj`  
 必須です。  `Number` オブジェクト。  
  
 `precision`  
 省略可能です。  有効桁数を指定します。  1 ～ 21 の範囲で指定します。  
  
## 戻り値  
 指数表記の数値では、\(`precision` \- 1\) 桁を小数点以下の数値として返します。  固定小数点表記の数値では、`precision` が有効桁数が返されます。  
  
 `precision` を指定しない場合、または **undefined** である場合は、**toString** メソッドが代わりに呼び出されます。  
  
## 使用例  
 `toPrecision` の使用例を次のコードに示します。  
  
```javascript  
var num = new Number(123);  
var prec = num.toPrecision();  
document.write(prec);  
document.write("<br/>");  
  
num = new Number(123.456);  
prec = num.toPrecision(5);  
document.write(prec);  
  
// Output:  
// 123  
// 123.46  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **対象**: [Number オブジェクト](../../javascript/reference/number-object-javascript.md)  
  
## 参照  
 [toFixed メソッド \(Number\)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toExponential メソッド \(Number\)](../../javascript/reference/toexponential-method-number-javascript.md)