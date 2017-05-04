---
title: "数字が必要です。 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5001"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b272f51a-97c2-4398-8b46-9cc49a5c0bd6
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 数字が必要です。
**Number** 以外の型のオブジェクトに対して **Number.prototype.toString** メソッドまたは **Number.prototype.valueOf** メソッドを呼び出そうとしました。  この種類の呼び出しに対するオブジェクトは、**Number** 型でなければなりません。  
  
### このエラーを解決するには  
  
-   **Number.prototype.toString** メソッドまたは **Number.prototype.valueOf** メソッドは、**Number** 型のオブジェクトに対してのみ呼び出してください。  
  
## 参照  
 [Number オブジェクト](../../javascript/reference/number-object-javascript.md)   
 [number プロパティ \(Error\)](../../javascript/reference/number-property-error-javascript.md)