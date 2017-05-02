---
title: "ビットごとの NOT 演算子 (~) (JavaScript) | Microsoft Docs"
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
  - "~"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ビット処理演算子, NOT 演算子"
  - "NOT 演算子"
ms.assetid: 39f92474-fe05-4a8b-9ad8-caca93f82bca
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# ビットごとの NOT 演算子 (~) (JavaScript)
式で指定された値のビットごとの NOT \(否定\) 演算を実行します。  
  
## 構文  
  
```  
  
result = ~ expression  
```  
  
## パラメーター  
 *result*  
 任意の変数を指定します。  
  
 *expression*  
 任意の式を指定します。  
  
## 解説  
 単項演算子での式の評価は、`~` 演算子も含めてすべて次のように行われます。  
  
-   undefined または `null` を持つ式を指定すると、ランタイム エラーが発生します。  
  
-   オブジェクトは文字列に変換されます。  
  
-   文字列は、数値に変換されます。  数値に変換できない場合は、実行時エラーが発生します。  
  
-   ブール値は数値として扱われます \(偽の場合は 0、真の場合は 1\)。  
  
 演算子は、結果として導かれた数値に適用されます。  
  
 `~` 演算子は、式の値を 2 進数形式で取り込み、その各ビットを反転させます。  
  
 元の式でビットが 1 の場合は必ず 0 になります。  元の式でビットが 0 の場合は必ず 1 になります。  
  
 ビットごとの NOT \(~\) 演算子の使用例を次に示します。  
  
```  
var temp = ~5;  
```  
  
 結果値は、次の表に示すように、\-6 です。  
  
|式|バイナリ値 \(2 の補数\)|10 進形式での値|  
|-------|---------------------|---------------|  
|5|00000000 00000000 00000000 00000101|5|  
|~5|11111111 11111111 11111111 11111010|\-6|  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [論理 NOT 演算子 \(\!\)](../../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)