---
title: "コンマ演算子 (,) (JavaScript) | Microsoft Docs"
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
  - "%2C"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "コンマ演算子"
ms.assetid: 699fa0bf-cd0a-45ee-a291-2fbed4ecd470
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# コンマ演算子 (,) (JavaScript)
2 つの式を順番に実行します。  
  
## 構文  
  
```  
  
expression1, expression2  
```  
  
## パラメーター  
 `expression1`  
 任意の式を指定します。  
  
 `expression2`  
 任意の式を指定します。  
  
## 解説  
 `,` 演算子を使用すると、式が左から順に実行されます。  `,` 演算子が最もよく使用されるのは、`for` ループのインクリメント式の中です。  次に例を示します。  
  
```javascript  
j=25;  
for (i = 0; i < 10; i++, j++)  
{  
   k = i + j;  
}  
```  
  
 `for` ステートメントでは、ループ内の処理の最後に実行する式として指定できるのは単一の式だけです。  `,` 演算子では複数の式を単一の式として処理できるため、両方の変数をインクリメントできます。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [for ステートメント](../../javascript/reference/for-statement-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)