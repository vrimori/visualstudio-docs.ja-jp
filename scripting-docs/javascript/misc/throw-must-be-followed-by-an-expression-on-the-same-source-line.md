---
title: "Throw ステートメントに指定する式は、ソース コードの同一行に記述してください | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1035"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Throw ステートメントに指定する式は、ソース コードの同一行に記述してください
`throw` キーワードを使用しましたが、同じソース行に式を記述していません。  `throw` ステートメントは、`throw` キーワードおよびそれに続くスローする式の 2 つの部分で構成されます。  次に例を示します。  
  
```javascript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 この 2 つの部分を分割することはできません。  
  
### このエラーを解決するには  
  
-   `throw` キーワードとスローする式を同じ行に記述してください。  
  
## 参照  
 [Error オブジェクト](../../javascript/reference/error-object-javascript.md)   
 [throw ステートメント](../../javascript/reference/throw-statement-javascript.md)   
 [try...catch...finally ステートメント](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)