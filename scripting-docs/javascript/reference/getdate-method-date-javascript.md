---
title: "getDate メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "getDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date オブジェクト"
  - "日付、月の日を返す"
  - "getDate メソッド"
ms.assetid: 67e7f07c-dd46-4b42-82d6-e53e4bd33703
caps.latest.revision: 20
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 20
---
# getDate メソッド (Date) (JavaScript)
日付の日の部分を現地時刻で取得します。  
  
## 構文  
  
```  
  
dateObj.getDate()   
```  
  
#### パラメーター  
 `dateObj` 参照は必須で、`Date` オブジェクトを指定します。  
  
## 戻り値  
 日付の日の部分を表す 1 ～ 31 の整数を指定します。  
  
## 解説  
 日付の日の部分を世界協定時刻 \(UTC\) で取得するには、`getUTCDate` メソッドを使用します。  
  
## 使用例  
 `getDate` メソッドの使用例を次に示します。  
  
```javascript  
var date = new Date("Jan 01, 2001");  
var str = "Today's date is: ";  
   str += (date.getMonth() + 1) + "/";  
   str += date.getDate() + "/";  
   str += date.getFullYear();  
document.write(str);  
  
// Output: Today's date is: 1/1/2001  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getUTCDate メソッド \(Date\)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate メソッド \(Date\)](../../javascript/reference/setdate-method-date-javascript.md)   
 [setUTCDate メソッド \(Date\)](../../javascript/reference/setutcdate-method-date-javascript.md)