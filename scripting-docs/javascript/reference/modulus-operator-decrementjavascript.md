---
title: "剰余演算子 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "%"
dev_langs: 
  - "JavaScript"
  - "DHTML"
helpviewer_keywords: 
  - "剰余演算子、JavaScript"
  - "% 演算子 [JavaScript]"
  - "剰余関数 [JavaScript]"
ms.assetid: 087d654f-623b-498d-95ff-596d26bf674d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 剰余演算子 (JavaScript)
1 つの式の値を他方で除算し、その剰余を返します。  
  
## 構文  
  
```  
  
result = number1 % number2  
```  
  
## 引数  
 `result`  
 任意の変数を指定します。  
  
 `number1`  
 任意の数式を指定します。  
  
 `number2`  
 任意の数式を指定します。  
  
## 解説  
 剰余演算子は、引数 `number1` を引数 `number2` で除算し、その剰余だけを `result` として返します。  `result` の符号は、`number1` の符号と同じです。  `result` の値は、0 から `number2` の絶対値の範囲になります。  
  
 剰余演算子の使用例を次のコードに示します。  
  
```  
var modResult = 19 % 6.7;  
document.write(modResult);  
  
// Output: 5.6  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)