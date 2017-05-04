---
title: "getUTCDay メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCDay"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date オブジェクト"
  - "日付、UTC"
  - "UTC 日付、返す"
  - "getUTCDay メソッド"
ms.assetid: 2fceb5b0-6f77-4919-82c3-0877fd55bacb
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# getUTCDay メソッド (Date) (JavaScript)
世界協定時刻 \(UTC\) を使用して曜日を取得します。  
  
## 構文  
  
```  
  
dateObj.getUTCDay()   
```  
  
#### パラメーター  
 `dateObj` 参照は必須で、`Date` オブジェクトを指定します。  
  
## 戻り値  
 曜日を表す 0 \(日曜日\) ～ 6 \(土曜日\) の整数を返します。  
  
## 解説  
 現地時刻を使用して曜日を取得するには、`getDate` メソッドを使用します。  
  
## 使用例  
 `getUTCDay` メソッドを使用する方法の例を次に示します。  
  
```javascript  
var date = new Date("2/6/2001");  
var day = date.getUTCDay();  
document.write(day);  
  
// Output: 2  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getDay メソッド \(Date\)](../../javascript/reference/getday-method-date-javascript.md)