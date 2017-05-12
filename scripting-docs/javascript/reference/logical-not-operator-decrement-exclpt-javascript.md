---
title: "論理 NOT 演算子 (!)(JavaScript) | Microsoft Docs"
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
  - "!"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "! 演算子"
  - "! 演算子, 概要 (! 演算子の)"
  - "論理 NOT 演算子"
ms.assetid: 68c3dc71-ae95-4293-9155-67405846d71d
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 論理 NOT 演算子 (!)(JavaScript)
式で指定された値の論理否定を求めます。  
  
## 構文  
  
```  
  
result = !expression  
```  
  
## パラメーター  
 *result*  
 任意の変数を指定します。  
  
 *expression*  
 任意の式を指定します。  
  
## 解説  
 *result* がどのように決定されるかを次の表に示します。  
  
|`expression` の値|`result` の値|  
|---------------------|-----------------|  
|True|False|  
|False|True|  
  
 **\!** 演算子などの単項演算子での式の評価はすべて次のように行われます。  
  
-   undefined または `null` を持つ式を指定すると、ランタイム エラーが発生します。  
  
-   オブジェクトは文字列に変換されます。  
  
-   文字列は、数値に変換されます。  数値に変換できない場合は、実行時エラーが発生します。  
  
-   ブール値は数値として扱われます \(偽の場合は 0、真の場合は 1\)。  
  
 演算子は、結果として導かれた数値に適用されます。  
  
 **\!** 演算子では、*expression* が 0 以外の値の場合、*result* は 0 になります。  *expression* が 0 の場合、*result* は 1 になります。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [ビットごとの NOT 演算子 \(~\)](../../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)