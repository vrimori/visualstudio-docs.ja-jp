---
title: "ビットごとの OR 代入演算子 (|=) (JavaScript) | Microsoft Docs"
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
  - "|="
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "|= 演算子"
  - "代入演算子, ビットごと [JavaScript]"
  - "ビット処理演算子, OR 演算子"
  - "OR 演算子"
ms.assetid: 9b424ff6-4442-4621-b3b6-83e7fd1e5cd5
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# ビットごとの OR 代入演算子 (|=) (JavaScript)
変数の値と式で指定された値のビットごとに OR 演算を行い、その結果を変数に代入します。  
  
## 構文  
  
```  
  
result |= expression  
```  
  
## パラメーター  
 *result*  
 任意の変数を指定します。  
  
 *expression*  
 任意の式を指定します。  
  
## 解説  
 この演算子は、次のように指定するのと同じです。  
  
```javascript  
result = result | expression  
```  
  
 **&#124;\=** 演算子は *result* 値と *expression* 値のバイナリ表現をチェックし、それに対してビットごとの OR 演算を行います。  この演算の結果は次のようになります。  
  
```javascript  
0101    (result)  
1100    (expression)  
----  
1101    (output)  
```  
  
 どちらか一方の式でビットの値が 1 の場合、演算結果のそのビットの値は 1 になります。  それ以外の場合は 0 になります。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [ビットごとの OR 演算子 \(&#124;\)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)