---
title: "toString メソッド (配列) | Microsoft Docs"
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
ms.assetid: 71fbea85-3e00-41b0-b167-25e4281e5e8a
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# toString メソッド (配列)
配列の文字列表現を返します。  
  
## 構文  
  
```  
  
array.toString()  
```  
  
## パラメーター  
 `array`  
 必須です。  文字列として表示する配列を指定します。  
  
## 戻り値  
 配列の文字列表現。  
  
## 解説  
 `Array` の要素は、文字列に変換されます。  結果の文字列は、コンマによって連結および区切られます。  
  
## 使用例  
 配列を使用した **toString** メソッドの例を次に示します。  
  
```javascript  
var arr = [1, 2, 3, 4];  
var s = arr.toString();  
document.write(s);  
  
// Output: 1,2,3,4  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]