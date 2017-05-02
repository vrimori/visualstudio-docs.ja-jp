---
title: "isFinite 関数 (JavaScript) | Microsoft Docs"
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
  - "isFinite"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "有限数"
  - "isFinite メソッド"
ms.assetid: ea9287d2-892f-496b-86b7-f9196868d5cf
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# isFinite 関数 (JavaScript)
指定した数値が有限かどうかを判定します。  
  
## 構文  
  
```  
isFinite(number)   
```  
  
## 解説  
 必須の `number` 引数には、任意の数値を指定します。  
  
 `isFinite` 関数は、`number` 引数に指定した値が `NaN`、負の無限大、正の無限大のいずれでもない場合に `true` を返します。  いずれかに該当する場合は、**false** を返します。  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Global オブジェクト](../../javascript/reference/global-object-javascript.md)  
  
## 参照  
 [isNaN 関数](../../javascript/reference/isnan-function-javascript.md)