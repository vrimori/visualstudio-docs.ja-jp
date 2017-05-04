---
title: "減算演算子 (-) (JavaScript) | Microsoft Docs"
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
  - "-"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "- 演算子"
  - "- 演算子, - 演算子の概要"
  - "算術演算子, 減算"
  - "否定演算子"
  - "演算子, 減算"
  - "減算演算子, 構文"
ms.assetid: cd0681d3-15cd-49fe-b4dd-e087de55d778
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 減算演算子 (-) (JavaScript)
一方の式の値から他方の式の値を減算します。または単一の式の単項否定 \(符号を反転した値\) を求めます。  
  
## 構文  
  
```  
  
result = number1 - number2;  
  
```  
  
## パラメーター  
 *result*  
 任意の数値変数を指定します。  
  
 `number`  
 任意の数式を指定します。  
  
 `number1`  
 任意の数式を指定します。  
  
 `number2`  
 任意の数式を指定します。  
  
## 解説  
 構文 1 では、**\-** 演算子は、減算演算子として 2 つの数値の差を求めるために使用されます。  構文 2 では、**\-** 演算子は、単項マイナス符号演算子として式の符号を反転した値 \(数値の負の値\) を指定するために使用されます。  
  
 構文 2 の場合には、他のすべての単項演算子の場合と同様、式の評価は次のように行われます。  
  
-   undefined または `null` を持つ式を指定すると、ランタイム エラーが発生します。  
  
-   オブジェクトは文字列に変換されます。  
  
-   文字列は、数値に変換されます。  数値に変換できない場合は、実行時エラーが発生します。  
  
-   ブール値は数値として扱われます \(偽の場合は 0、真の場合は 1\)。  
  
 演算子は、結果として導かれた数値に適用されます。  構文 2 で、対象の数値が 0 以外の場合は *result* が元の値の符号を反転させた値になります。  対象の数値が 0 の場合は、*result* も 0 になります。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [減算代入演算子 \(\-\=\)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)