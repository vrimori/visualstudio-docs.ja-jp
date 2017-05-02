---
title: "toString メソッド (文字列) | Microsoft Docs"
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
ms.assetid: 56178c6e-cb08-4b34-824c-f63505379952
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# toString メソッド (文字列)
文字列の文字列表現を返します。  
  
## 構文  
  
```  
  
string.toString()  
```  
  
## パラメーター  
 `string`  
 必須です。  文字列として表示する配列を指定します。  
  
## 戻り値  
 文字列の文字列表現。  
  
## 使用例  
 文字列を使用した **toString** メソッドの例を次に示します。  
  
```javascript  
var string = "this is a test";  
var strStr = string.toString();  
document.write(strStr);  
  
// Output: this is a test  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]