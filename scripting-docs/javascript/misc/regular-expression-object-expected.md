---
title: "Regular Expression オブジェクトが必要です。 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5016"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: e226096c-c58f-4bcb-a71e-fa32ce474b67
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Regular Expression オブジェクトが必要です。
`RegExp` 以外の型のオブジェクトに対して **RegExp.prototype.toString** メソッドまたは **RegExp.prototype.valueOf** メソッドを呼び出そうとしました。  この種類の呼び出しに対するオブジェクトは、`RegExp` 型にする必要があります。  
  
### このエラーを解決するには  
  
-   **RegExp.prototype.toString** メソッドまたは **RegExp.prototype.valueOf** メソッドは、`RegExp` 型のオブジェクトのみに対して呼び出します。  
  
## 参照  
 [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ja-jp/ab0766e1-7037-45ed-aa23-706f58358c0e)