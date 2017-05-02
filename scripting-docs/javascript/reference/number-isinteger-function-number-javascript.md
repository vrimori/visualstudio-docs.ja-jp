---
title: "Number.isInteger 関数 (Number) (JavaScript) | Microsoft Docs"
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
ms.assetid: 54fcf68c-0067-4bad-af94-d7ff8c88914a
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Number.isInteger 関数 (Number) (JavaScript)
値が整数であるかどうかを示すブール値を返します。  
  
## 構文  
  
```  
Number.isInteger(numValue)   
```  
  
## 戻り値  
 値が整数である場合は `true` を返します。それ以外の場合は `false` を返します。  
  
## 解説  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **対象**: [Number オブジェクト](../../javascript/reference/number-object-javascript.md)  
  
## 使用例  
  
```javascript  
// Returns true  
Number.isInteger(100)  
Number.isInteger(-100)  
  
// Returns false  
Number.isInteger(Number.NaN)  
Number.isInteger(Infinity)  
Number.isInteger(100 / 3)  
Number.isInteger("100")  
  
```