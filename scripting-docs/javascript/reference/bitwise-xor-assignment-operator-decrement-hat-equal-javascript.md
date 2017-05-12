---
title: "ビットごとの XOR 代入演算子 (^=) (JavaScript) | Microsoft Docs"
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
  - "^="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "^= 演算子"
  - "^= 演算子, ^= 演算子の概要"
  - "代入演算子, ビットごと [JavaScript]"
  - "ビット処理演算子, XOR 演算子"
  - "XOR 演算子"
ms.assetid: a6ded216-27b6-4fc4-a51b-7d10cc6f820c
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# ビットごとの XOR 代入演算子 (^=) (JavaScript)
変数と式に対してビットごとの排他的 OR 演算を実行し、その結果を変数に代入します。  
  
## 構文  
  
```  
  
result ^= expression  
```  
  
## パラメーター  
 *result*  
 任意の変数を指定します。  
  
 *expression*  
 任意の式を指定します。  
  
## 解説  
 **^\=** 演算子は、次のように指定するのとまったく同じです。  
  
```javascript  
result = result ^ expression  
```  
  
 **^\=**演算子は、2 つの式の値をバイナリ表現で取り込み、それに対してビットごとの排他的 OR 演算を実行します。  この演算の結果は次のようになります。  
  
```javascript  
0101    (result)  
1100    (expression)  
----  
1001    (result)  
```  
  
 一方の式だけでビットの値が 1 の場合、演算結果のそのビットの値は 1 になります。  それ以外の場合は 0 になります。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [ビットごとの XOR 演算子 \(^\)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)