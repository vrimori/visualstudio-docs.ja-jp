---
title: "文字セットの範囲が無効です (JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5021"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 971e9d5a-f88a-47a8-af94-f3c7c4aed5ab
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# 文字セットの範囲が無効です (JavaScript)
無効な文字セットの範囲を使用して正規表現を作成しようとしました。  文字セットは a\-z、0\-9 などのように単一の文字だけで範囲を指定する必要があります。文字セットに \\w などの文字クラスを含めることはできません。  範囲の最初の文字は、範囲の 2 番目の文字の前に記述する必要があります。  次に例を示します。  
  
```javascript  
var good = /[a-z]/;     // A valid character range - a comes before z.  
var notGood = /[z-a]/;  // An invalid character range - z does not come before a.  
```  
  
### このエラーを解決するには  
  
-   正規表現の文字セットは単一の文字だけを使用して構成し、正しい順序で記述します。  
  
## 参照  
 [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ja-jp/ab0766e1-7037-45ed-aa23-706f58358c0e)