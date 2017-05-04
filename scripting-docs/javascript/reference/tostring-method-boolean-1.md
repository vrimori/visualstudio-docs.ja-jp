---
title: "toString メソッド (Boolean) | Microsoft Docs"
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
ms.assetid: c46b43c0-6946-407a-b0e0-49cba90e226a
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# toString メソッド (Boolean)
オブジェクトの値を表す文字列を返します。  
  
## 構文  
  
```  
  
boolean.toString()  
```  
  
## パラメーター  
 `boolean`  
 必須です。  文字列表現を取得するオブジェクトを指定します。  
  
## 戻り値  
 ブール値が `true` の場合、"true" という文字列を返します。  それ以外の場合は、"false" を返します。  
  
## 解説  
  
## 使用例  
 **toString** メソッドの使用例を次に示します。  
  
```javascript  
var s = new Boolean(0);  
document.write(s.toString());  
  
// Output: false;  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]