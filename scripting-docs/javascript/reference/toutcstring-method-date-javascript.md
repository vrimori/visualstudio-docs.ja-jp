---
title: "toUTCString メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "toUTCString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toUTCString メソッド"
  - "UTC 日付, 変換 (文字列に)"
ms.assetid: eb0983ed-7884-42fa-a2cc-de92b3111207
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toUTCString メソッド (Date) (JavaScript)
日付を世界協定時刻 \(UTC\) の文字列に変換します。  
  
## 構文  
  
```  
  
dateObj.toUTCString()   
```  
  
## 解説  
 必須の `dateObj` 参照には、任意の `Date` オブジェクトを指定します。  
  
 `toUTCString` メソッドは、世界協定時刻 \(UTC\) を表す `String` オブジェクトを返します。  
  
## 使用例  
 `toUTCString` メソッドの使用例を次に示します。  
  
```javascript  
function toUTCStrDemo(){  
   var d, s;                   //Declare variables.  
   d = new Date();             //Create Date object.  
   s = "Current setting is ";  
   s += d.toUTCString();       //Convert to UTC string.  
   return(s);                  //Return UTC string.  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [toGMTString メソッド \(Date\)](../../javascript/reference/togmtstring-method-date-javascript.md)