---
title: "Math.random 関数 (JavaScript) | Microsoft Docs"
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
  - "random"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Math オブジェクト"
  - "擬似乱数"
  - "random メソッド"
ms.assetid: a28c5c66-c42f-4082-9b71-9a5ee4652cd7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Math.random 関数 (JavaScript)
0 ～ 1 の範囲の擬似乱数を返します。  
  
## 構文  
  
```  
  
Math.random( )  
  
```  
  
## 解説  
 生成される擬似乱数は 0 ～ 1 の範囲内の値になります \(0 は含まれ、1 は含まれません\)。つまり、戻り値が 0 になることはあっても 1 になることはありません。  乱数ジェネレーターのシードは、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] が初めて読み込まれた時点で自動的に生成されます。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [Math オブジェクト](../../javascript/reference/math-object-javascript.md)  
  
## 参照  
 [Math.pow 関数](../../javascript/reference/math-pow-function-javascript.md)