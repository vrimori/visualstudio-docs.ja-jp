---
title: "ビットごとの AND 演算子 (&amp;) (JavaScript) | Microsoft Docs"
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
  - "&"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "代入演算子、ビットごとの [JavaScript]"
  - "& 演算子、& 演算子の概要"
  - "AND 演算子"
  - "& 演算子"
  - "ビット処理演算子、AND 演算子"
  - "& 演算子、ビット処理演算子"
ms.assetid: a8c17a55-2599-4518-98d7-671699f4d5f3
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# ビットごとの AND 演算子 (&amp;) (JavaScript)
2 つの 32 ビット式のビットごとの AND 演算を実行します。  
  
## 構文  
  
```  
  
result = expression1 & expression2  
```  
  
## パラメーター  
 `result`  
 演算の結果。  
  
 `expression1`  
 任意の式を指定します。  
  
 `expression2`  
 任意の式を指定します。  
  
## 解説  
 `&` は、2 個の 32 ビット式のそれぞれのビットに対してビットごとの AND 演算を実行します。  ビットの両方が 1 の場合、結果は 1 です。  それ以外の場合、結果は 0 になります。  
  
|Bit1|Bit2|ANDed 値|  
|----------|----------|-------------|  
|0|0|0|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
  
 `&` 演算子を使用する方法の例を次に示します。  
  
```javascript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
var result = expr1 & expr2;  
  
document.write(result);  
// Output: 1  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [ビットごとの AND 代入演算子 \(&\=\)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)