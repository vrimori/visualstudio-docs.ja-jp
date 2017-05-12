---
title: "Math.sign 関数 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 8b462020-ceff-4947-8dd1-c78e6aff8d98
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Math.sign 関数 (JavaScript)
数値が正、負、または 0 のいずれであるかを示す、数値の符号を返します。  
  
## 構文  
  
```  
Math.sign(number)  
```  
  
## 解説  
 必須の `number` 引数は、符号を必要とする数値式です。  
  
 戻り値は次のいずれかになります。  
  
-   `number` が `NaN` の場合は `NaN`。  
  
-   `number` が −0 の場合は \-0。  
  
-   `number` が \+0 の場合は \+0。  
  
-   `number` が負の値で、−0 ではない場合は \-1。  
  
-   `number` が正の値で、\+0 ではない場合は \+1。  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]