---
title: "インクリメント演算子 (++)、デクリメント演算子 (--) (JavaScript) | Microsoft Docs"
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
  - "--"
  - "++"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "インクリメント演算子、構文"
  - "++ 演算子"
  - "++ 演算子、++ 演算子の概要"
  - "デクリメント演算子、構文"
  - "-- 演算子"
ms.assetid: 49eaf4cf-8818-478d-a429-cdd2ece20811
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# インクリメント演算子 (++)、デクリメント演算子 (--) (JavaScript)
インクリメント演算子は変数の値に 1 ずつ加算し、デクリメント演算子は変数を 1 ずつ減算します。  
  
## 構文  
  
```  
  
      result = ++variable  
result = --variable  
result = variable++  
result = variable--  
```  
  
## パラメーター  
 `result`  
 任意の変数を指定します。  
  
 `variable`  
 任意の変数を指定します。  
  
## 解説  
 演算子が変数の前にある場合、値は式が評価される前に変更されます。  演算子が変数の後ろにある場合、値は式が評価された後で変更されます。  つまり、`j = ++k;` である場合、`j` の値は `k` の初期値に 1 を加えたものです。`j = k++;` である場合は、`j` は `j` に割り当てられた後で増加する `k` の初期値です。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)