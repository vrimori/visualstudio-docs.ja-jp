---
title: "加算代入演算子 (+=) (JavaScript) | Microsoft Docs"
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
  - "+="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "加算代入演算子 (+=)"
  - "+= 演算子"
  - "代入演算子、JavaScript"
ms.assetid: 8517d05c-38b0-4107-bea4-253eb420f438
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 加算代入演算子 (+=) (JavaScript)
変数の値に式で指定された値を加算し、その結果を変数に代入します。  
  
## 構文  
  
```  
  
result += expression   
```  
  
## パラメーター  
 `result`  
 任意の変数を指定します。  
  
 `expression`  
 任意の式を指定します。  
  
## 解説  
 この演算子は、次のように指定するのと同じです。`result = result + expression`。  
  
 `+=` 演算子の動作は、指定する式の型によって決まります。  
  
|If|Then|  
|--------|----------|  
|両方とも数値またはブール値の場合|加算|  
|両方とも文字列の場合|連結|  
|一方が数値で他方が文字列の場合|連結|  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [加算演算子 \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)