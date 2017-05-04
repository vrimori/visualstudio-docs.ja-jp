---
title: "文字列が必要です。 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5005"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4c214c4b-9cd7-473b-8d90-2344c0375c25
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# 文字列が必要です。
`String` 以外の型のオブジェクトに対して **String.prototype.toString** メソッドまたは **String.prototype.valueOf** メソッドを呼び出そうとしました。  この種類の呼び出しに対するオブジェクトは、`String` 型にする必要があります。  
  
### このエラーを解決するには  
  
-   **String.prototype.toString** メソッドまたは **String.prototype.valueOf** メソッドは、`String` 型のオブジェクトのみに対して呼び出します。  
  
## 参照  
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)   
 [toString メソッド \(Object\)](../../javascript/reference/tostring-method-object-javascript.md)