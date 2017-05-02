---
title: "論理 AND 演算子 (&amp;&amp;) (JavaScript) | Microsoft Docs"
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
  - "&&"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "&& 演算子"
  - "論理 AND 演算子"
ms.assetid: 4714dea9-1999-444a-8acd-72f0851e4f65
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# 論理 AND 演算子 (&amp;&amp;) (JavaScript)
2 つの式について、論理積を実行します。  
  
## 構文  
  
```  
  
result = expression1 && expression2   
```  
  
## パラメーター  
 `result`  
 任意の変数。  
  
 `expression1`  
 任意の式。  
  
 `expression2`  
 任意の式。  
  
## 解説  
 `expression1` が `false` に評価された場合、`result` は `expression1` です。  それ以外の場合、`result` は `expression2` です。  その結果、両方のオペランドが true である場合は、`true` が返され、それ以外の場合は、`false` が返されます。  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] は次の規則を使用して、非ブール値をブール値に変換します。  
  
-   すべてのオブジェクトは、`true` と見なされます。  
  
-   文字列は、空である場合、`false` と見なされます。  
  
-   `null` と `undefined` は `false` と見なされます。  
  
-   数値は、ゼロである場合、`false` となります。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)