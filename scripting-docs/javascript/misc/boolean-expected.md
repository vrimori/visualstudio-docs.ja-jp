---
title: "ブール型 (Boolean) が必要です。 | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5010"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 35d71b7f-53fd-44c4-a7c7-b1550c65cfd4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# ブール型 (Boolean) が必要です。
`Boolean` 以外の型のオブジェクトに対して **Boolean.prototype.toString** メソッドまたは **Boolean.prototype.valueOf** メソッドを呼び出そうとしました。  この種類の呼び出しに対するオブジェクトは、`Boolean` 型にする必要があります。  次に例を示します。  
  
```javascript  
var o = new Object;  
o.f = Boolean.prototype.toString;  
o.f();  
```  
  
### このエラーを解決するには  
  
-   **Boolean.prototype.toString** メソッドまたは **Boolean.prototype.valueOf** メソッドは、**Boolean** 型のオブジェクトに対してのみ呼び出してください。  
  
## 参照  
 [Boolean オブジェクト](../../javascript/reference/boolean-object-javascript.md)   
 [データ型](../../javascript/data-types-javascript.md)   
 [プログラム フローの制御](../../javascript/controlling-program-flow-javascript.md)   
 [データのコピー、受け渡し、および比較](../../javascript/advanced/copying-passing-and-comparing-data-javascript.md)