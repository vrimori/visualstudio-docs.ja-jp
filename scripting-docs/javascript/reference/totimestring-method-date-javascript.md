---
title: "toTimeString メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "toTimeString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toTimeString メソッド"
ms.assetid: a4a8c0f2-55a9-4e84-94c3-f0a547fb04b5
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toTimeString メソッド (Date) (JavaScript)
時刻を文字列値として返します。  
  
## 構文  
  
```  
  
objDate. toTimeString( )  
```  
  
## 解説  
 `objDate` 参照は必須で、`Date` オブジェクトを指定します。  
  
 `toTimeString` メソッドは、現在のタイムゾーンの時刻を含む文字列値を返します。  
  
## 使用例  
 次の例では、時刻は、UTC の 1970 年 1 月 1 日 0 時から 2000 ミリ秒後に設定されて書き出されます。  
  
```javascript  
var aDate = new Date();  
     aDate.setTime(2000);  
     document.write(aDate.toTimeString());  
  
// Output depends on the time in the current time zone.  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 参照  
 [toDateString メソッド \(Date\)](../../javascript/reference/todatestring-method-date-javascript.md)   
 [toLocaleTimeString メソッド \(Date\)](../../javascript/reference/tolocaletimestring-method-date-javascript.md)