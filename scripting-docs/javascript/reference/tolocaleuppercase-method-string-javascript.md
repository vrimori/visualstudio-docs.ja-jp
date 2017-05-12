---
title: "toLocaleUpperCase メソッド (String) (JavaScript) | Microsoft Docs"
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
  - "toLocaleUpperCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleUpperCase メソッド"
ms.assetid: e927adb6-475e-44b2-91f7-cedda10a39b0
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# toLocaleUpperCase メソッド (String) (JavaScript)
ホスト環境の現在のロケールに従って、すべての英字を大文字に変換した文字列を返します。  
  
## 構文  
  
```  
  
stringVar.toLocaleUpperCase( )  
```  
  
## 解説  
 必須の `stringVar` 参照は、`String` オブジェクトまたはリテラル文字列です。  
  
 `toLocaleUpperCase` メソッドは、ホスト環境の現在のロケールに従って、文字列の文字を変換します。  ほとんどの場合、結果は `toUpperCase` メソッドの結果と同じになります。  結果が異なるのは、言語規則が通常の Unicode の大文字小文字のマッピングと競合する場合です。  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **対象**: [String オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## 参照  
 [toLocaleLowerCase メソッド \(String\)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [toUpperCase メソッド \(String\)](../../javascript/reference/touppercase-method-string-javascript.md)