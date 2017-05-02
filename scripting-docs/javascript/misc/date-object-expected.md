---
title: "Date オブジェクトが必要です。 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5006"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: d6ab82e6-ca64-46b4-a06c-5c6b0aa057cb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Date オブジェクトが必要です。
`Date` 型以外の型のオブジェクトに対して、**Date.prototype.toString** メソッドまたは **Date.prototype.valueOf** メソッドを呼び出そうとしました。  この種類の呼び出しに対するオブジェクトは、`Date` 型にする必要があります。  次に例を示します。  
  
```javascript  
var o = new Object;  
o.f = Date.prototype.toString;  
o.f();  
```  
  
### このエラーを解決するには  
  
-   **Date.prototype.toString** メソッドまたは **Date.prototype.valueOf** メソッドは、`Date` 型のオブジェクトのみに対して呼び出します。  
  
## 参照  
 [Date オブジェクト](../../javascript/reference/date-object-javascript.md)   
 [getDate メソッド \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [組み込みオブジェクト](../../javascript/intrinsic-objects-javascript.md)