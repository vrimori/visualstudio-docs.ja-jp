---
title: "toLowerCase メソッド (JavaScript) | Microsoft Docs"
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
  - "toLowerCase"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLowerCase メソッド"
ms.assetid: dfd543b9-3e7a-4f83-a391-9cde109ad6bc
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# toLowerCase メソッド (JavaScript)
文字列内のすべての英字を小文字に変換します。  
  
## 構文  
  
```  
  
        strVariable.toLowerCase()  
"String Literal".toLowerCase()   
```  
  
## 解説  
 `toLowerCase` メソッドは、英字だけに有効です。  
  
 `toLowerCase` メソッドの使用例を次に示します。  
  
```javascript  
var str1 = "This is a STRING.";  
var str2 = str1. toLowerCase();  
document.write(str2);  
  
// Output: this is a string.  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Applies To**: [String オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## 参照  
 [toLocaleLowerCase メソッド \(String\)](../../javascript/reference/tolocalelowercase-method-string-javascript.md)   
 [toUpperCase メソッド \(String\)](../../javascript/reference/touppercase-method-string-javascript.md)