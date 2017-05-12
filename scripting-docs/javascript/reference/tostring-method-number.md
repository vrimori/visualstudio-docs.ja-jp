---
title: "toString メソッド (数値) | Microsoft Docs"
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
ms.assetid: 07c3484b-d9d8-4451-a2be-88a19a081966
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# toString メソッド (数値)
数値の文字列表現を返します。  
  
## 構文  
  
```  
  
number.toString()  
```  
  
## パラメーター  
 `number`  
 必須です。  文字列として表示する数値を指定します。  
  
## 戻り値  
 数値の文字列表現。  
  
## 使用例  
 数値を使用した **toString** メソッドの例を次に示します。  
  
```javascript  
var number = 234.567;  
var s = number.toString();  
document.write(s.length);  
  
// Output: 7  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]