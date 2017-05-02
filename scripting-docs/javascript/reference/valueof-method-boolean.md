---
title: "valueOf メソッド (Boolean) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ac6ad343-7663-406a-a2b7-4cc5025ca3d6
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf メソッド (Boolean)
指定されたブールのプリミティブ値を返します。  
  
## 構文  
  
```  
  
boolean.valueOf()  
```  
  
## 戻り値  
 ブールのプリミティブ値 \(true または false\) を返します。  
  
## 解説  
 このメソッドの使用例を次のコードに示します。  
  
```javascript  
var bool = new Boolean("true");  
var s = bool.valueOf();  
document.write(s);  
  
// Output: true  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]