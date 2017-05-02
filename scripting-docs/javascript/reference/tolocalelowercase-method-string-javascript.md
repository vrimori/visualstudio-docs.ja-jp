---
title: "toLocaleLowerCase メソッド (String) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "toLocaleLowerCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleLowerCase メソッド"
ms.assetid: add894d3-d14a-4dbc-a9b9-7ad1d3a2e581
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# toLocaleLowerCase メソッド (String) (JavaScript)
ホスト環境の現在のロケールに従って、すべての英字を小文字に変換します。  
  
## 構文  
  
```  
  
stringVar.toLocaleLowerCase( )  
```  
  
## 解説  
 必須の `stringVar` 参照は、`String` オブジェクトまたはリテラル文字列です。  
  
 `toLocaleLowerCase` メソッドは、ホスト環境の現在のロケールに従って、文字列の文字を変換します。  ほとんどの場合、結果は `toLowerCase` のメソッドの結果と同じになります。  結果が異なるのは、言語規則が通常の Unicode の大文字小文字のマッピングと競合する場合です。  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **対象**: [String オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## 参照  
 [toLocaleUpperCase メソッド \(String\)](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)   
 [toLowerCase メソッド](../../javascript/reference/tolowercase-method-javascript.md)