---
title: "論理 OR 演算子 (||) (JavaScript) | Microsoft Docs"
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
  - "||"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "|| 演算子"
  - "論理 OR 演算子"
ms.assetid: 95295331-6269-4311-8391-dc1c68e116ab
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# 論理 OR 演算子 (||) (JavaScript)
2 つの式の論理和を求めます。  
  
## 構文  
  
```  
  
result = expression1 || expression2  
```  
  
## パラメーター  
 *result*  
 任意の変数を指定します。  
  
 *expression1*  
 任意の式を指定します。  
  
 *expression2*  
 任意の式を指定します。  
  
## 解説  
 2 つの式のどちらか一方、または両方が **True** の場合、*result* は **True** になります。  *result* がどのように決定されるかを次の表に示します。  
  
|`expression1` の値|`expression2` の値|`result` の値|  
|----------------------|----------------------|-----------------|  
|True|True|True|  
|True|False|True|  
|False|True|True|  
|False|False|False|  
  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] では、非ブール値がブール値に変換される場合に、次の規則が適用されます。  
  
-   オブジェクトはすべて true となります。  
  
-   文字列は、長さ 0 の文字列の場合だけ偽 \(false\) となります。  
  
-   `null` と未定義では false となります。  
  
-   数値は 0 の場合だけ false となります。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 \(JavaScript\)](../../javascript/misc/operator-subtractsummary-javascript.md)