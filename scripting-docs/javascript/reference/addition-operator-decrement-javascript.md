---
title: "加算演算子 (+) (JavaScript) | Microsoft Docs"
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
  - "+"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "算術演算子、加算"
  - "文字列 [Visual Studio]、連結"
  - "連結演算子、および加算演算子"
  - "加算演算子"
  - "+ 演算子"
ms.assetid: ec1237d3-e78b-4e77-bd7d-c0204cf03acd
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 加算演算子 (+) (JavaScript)
一方の数式の値を他方に加算します。または 2 つの文字列を連結します。  
  
## 構文  
  
```  
  
result = expression1 + expression2  
```  
  
## パラメーター  
 `result`  
 任意の変数を指定します。  
  
 `expression1`  
 任意の式を指定します。  
  
 `expression2`  
 任意の式を指定します。  
  
## 解説  
 **\+** 演算子の動作は、指定する 2 つの式の型によって決まります。  
  
|If|Then|  
|--------|----------|  
|両方とも数値またはブール値の場合|加算|  
|両方とも文字列の場合|連結|  
|一方が数値で他方が文字列の場合|連結|  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [加算代入演算子 \(\+\=\)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)