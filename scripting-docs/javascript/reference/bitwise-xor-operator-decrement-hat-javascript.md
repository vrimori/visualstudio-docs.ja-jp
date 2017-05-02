---
title: "ビットごとの XOR 演算子 (^) (JavaScript) | Microsoft Docs"
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
  - "^"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ビット処理演算子, XOR 演算子"
  - "XOR 演算子"
ms.assetid: 44ef0d18-abb5-4d83-9e77-6394635b3f48
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# ビットごとの XOR 演算子 (^) (JavaScript)
2 つの式のビットごとの XOR \(排他的論理和\) 演算を実行します。  
  
## 構文  
  
```  
  
result = expression1 ^ expression2  
```  
  
## パラメーター  
 *result*  
 任意の変数を指定します。  
  
 *expression1*  
 任意の式を指定します。  
  
 *expression2*  
 任意の式を指定します。  
  
## 解説  
 **^** 演算子は、2 つの式の値をバイナリ表現で取り込み、それに対してビットごとの排他的 OR 演算を実行します。  この演算の結果は次のようになります。  
  
```javascript  
0101   (expression1)  
1100   (expression2)  
----  
1001   (result)  
```  
  
 一方の式だけでビットの値が 1 の場合、演算結果のそのビットの値は 1 になります。  それ以外の場合は 0 になります。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [ビットごとの XOR 代入演算子 \(^\=\)](../../javascript/reference/bitwise-xor-assignment-operator-decrement-hat-equal-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)