---
title: "valueOf メソッド (数値) | Microsoft Docs"
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
ms.assetid: 0242a9ce-d41a-4c9b-af59-e8df32bbd913
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# valueOf メソッド (数値)
指定された数値のプリミティブ値を返します。  
  
## 構文  
  
```  
  
number.valueOf()  
```  
  
#### パラメーター  
 このメソッドにパラメーターはありません。  
  
## 戻り値  
 数値を返します。  
  
## 解説  
 インスタンス化された数値オブジェクトがこのメソッドの戻り値と同じである例を次に示します。  
  
```javascript  
var num = 1234;  
var s = num.valueOf();  
  
if (num === s)  
document.write("same");  
else  
document.write("different");  
  
// Output:  
// same  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]