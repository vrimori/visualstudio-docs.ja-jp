---
title: "toFixed メソッド (Number) (JavaScript) | Microsoft Docs"
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
  - "toFixed"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toFixed メソッド"
ms.assetid: b5f03400-865e-4ab2-818c-f734c0f6d6f0
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# toFixed メソッド (Number) (JavaScript)
固定小数点表記の数を表します。  
  
## 構文  
  
```  
  
numObj.toFixed([fractionDigits])  
```  
  
## Parameters  
 `numObj`  
 必須。`Number` オブジェクトを指定します。  
  
 `fractionDigits`  
 Optional.  小数点以下の桁数を指定します。  0 ～ 20 の範囲で指定します。  
  
## 戻り値  
 小数点以下 `fractionDigits` 桁を含む数値を固定小数点表記で表した文字列を返します。  
  
 `fractionDigits` を指定していない場合、または **undefined** である場合、既定値は 0 です。  
  
## 使用例  
 `toFixed` の使用例を次のコードに示します。  
  
```javascript  
var num = new Number(123);  
var fix = num.toFixed();  
document.write(fix);  
document.write("<br/>");  
  
num = new Number(123.456);  
fix = num.toFixed(5);  
document.write(fix);  
  
// Output:  
// 123  
123.45600  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **対象**: [Number オブジェクト](../../javascript/reference/number-object-javascript.md)  
  
## 参照  
 [toExponential メソッド \(Number\)](../../javascript/reference/toexponential-method-number-javascript.md)   
 [toPrecision メソッド \(Number\)](../../javascript/reference/toprecision-method-number-javascript.md)