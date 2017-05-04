---
title: "Number.isSafeInteger (Number) (JavaScript) | Microsoft Docs"
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
ms.assetid: c7ef6ce8-fe71-4e53-be44-4dd440aef21d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Number.isSafeInteger (Number) (JavaScript)
JavaScript で数値を安全に表現できるかどうかを示すブール値を返します。  
  
## 構文  
  
```  
Number.isSafeInteger(numValue)   
```  
  
## 戻り値  
 数値が `Number.MIN_SAFE_INTEGER` と `Number.MAX_SAFE_INTEGER` の間である場合 \(その数値である場合も含む\) は `true`、そうでない場合は `false`。  
  
## 解説  
 JavaScript での安全な整数は、なんらかの丸め処理が適用される前に IEEE 754 倍精度数であるものです。  
  
## 使用例  
  
```javascript  
// Returns true  
Number.isSafeInteger(-100)  
Number.isSafeInteger(9007199254740991)  
  
// Returns false  
Number.isSafeInteger(Number.NaN)  
Number.isSafeInteger(Infinity)  
Number.isSafeInteger("100")  
Number.isSafeInteger(9007199254740992);  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **対象**: [Number オブジェクト](../../javascript/reference/number-object-javascript.md)