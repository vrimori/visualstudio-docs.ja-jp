---
title: "比較演算子 (JavaScript) | Microsoft Docs"
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
  - "Comparison"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "比較演算子、スクリプト"
  - "大なり演算子"
  - "比較演算子"
  - "以上演算子"
  - "inequity 演算子"
  - "恒等演算子"
ms.assetid: 084f90f0-d010-47cf-96dd-13d637fc9b68
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# 比較演算子 (JavaScript)
比較結果を示すブール値を返します。  
  
## 構文  
  
```  
  
expression1 comparisonoperator expression2  
```  
  
## パラメーター  
 `expression1`  
 任意の式を指定します。  
  
 `comparisonoperator`  
 任意の比較演算子を指定します。  
  
 `expression2`  
 任意の式を指定します。  
  
## 解説  
 文字列式を比較する場合、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] では Unicode のコード順に基づいて比較します。  
  
 比較演算子の種類と値によって、`expression1` と `expression2` がどのように比較されるかを次に示します。  
  
 関係演算子: `<`、`>`、`<=`、`>=`  
  
-   `expression1` と `expression2` の両方を数値に変換しようとします。  
  
-   式が両方とも文字列の場合は文字列比較が行われます。  
  
-   どちらか一方の式が `NaN` の場合は `false` が返されます。  
  
-   負の 0 は、正の 0 と等しいと評価されます。  
  
-   負の無限大は、それ自身を含むすべての式よりも小さいと評価されます。  
  
-   正の無限大は、それ自身を含むすべての式よりも大きいと評価されます。  
  
 等値演算子: `==`、`!=`  
  
-   2 つの式のデータ型が異なる場合は、文字列型、数値型、ブール型の順に変換を試みます。  
  
-   `NaN` は、それ自身を含む、どのような値とも等しくないと評価されます。  
  
-   負の 0 は、正の 0 と等しいと評価されます。  
  
-   `null` は、`null` と `undefined` の両方と等しいと評価されます。  
  
-   2 つの値が同一の文字列である場合、等価な数値である場合、同じオブジェクトである場合、および同一のブール値である場合、これらの値は等しいと評価されます。また、2 つの値のデータ型が異なる場合に、データ型の変換を行ってこのうちのいずれかに当てはまれば、2 つの値は等しいと評価されます。  
  
-   上記以外の比較演算は等しくないと評価されます。  
  
 同値演算子: `===`、`!==`  
  
 これらの演算子は、等値演算子と同様に動作します。ただし、型変換は行われません。  両方の式の型は同じでない場合、これらの式は常に `false` を返します。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)