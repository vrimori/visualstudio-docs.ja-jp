---
title: "ビットごとの AND 代入演算子 (&amp;=) (JavaScript) | Microsoft Docs"
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
  - "&="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "&= 演算子"
  - "代入演算子、ビットごとの [JavaScript]"
  - "AND 演算子"
  - "ビット処理演算子、AND 演算子"
ms.assetid: e7e2eabb-4fc1-4fdc-9dd8-1e6d715371fa
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# ビットごとの AND 代入演算子 (&amp;=) (JavaScript)
ビットごとの AND 演算の結果を、変数の値および式の値に設定します。  変数と式は、32 ビット整数として扱われます。  
  
## 構文  
  
```  
  
result &= expression  
```  
  
## パラメーター  
 `result`  
 任意の変数を指定します。  
  
 `expression`  
 任意の式を指定します。  
  
## 解説  
 この演算子は、次のように指定するのと同じです。  
  
```javascript  
result = result & expression  
```  
  
 [ビットごとの AND 演算子 \(&\)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md) は、`result` と `expression` の値をバイナリ表現で取り込み、それに対してビットごとの AND 演算を実行します。  この演算の結果は次のようになります。  
  
```javascript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
expr1 &= expr2;  
  
document.write(expr1);  
  
```  
  
 両方の式でビットの値が 1 の場合、演算結果のそのビット値は必ず 1 になります。  それ以外の場合は 0 になります。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [ビットごとの AND 演算子 \(&\)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)