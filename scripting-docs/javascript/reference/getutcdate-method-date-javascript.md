---
title: "getUTCDate メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date オブジェクト"
  - "日付、UTC"
  - "UTC 日付、返す"
  - "getUTCDate メソッド"
ms.assetid: 9e4c763f-c94c-44c9-9684-cb632d75b62e
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# getUTCDate メソッド (Date) (JavaScript)
世界協定時刻 \(UTC\) を使用して日付の日の部分を取得します。  
  
## 構文  
  
```  
  
dateObj.getUTCDate()   
```  
  
#### パラメーター  
 `dateObj` 参照は必須で、`Date` オブジェクトを指定します。  
  
## 戻り値  
 日付の日の部分を表す 1 ～ 31 の整数を返します。  
  
## 解説  
 月の日付を現地時間で取得するには、`getDate` メソッドを使用します。  
  
## 使用例  
 `getUTCDate` メソッドを使用する方法の例を次に示します。  
  
```javascript  
var date = new Date("1/23/2001");  
document.write(date.getUTCDate());  
  
// Output: 23  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getDate メソッド \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [setDate メソッド \(Date\)](../../javascript/reference/setdate-method-date-javascript.md)   
 [setUTCDate メソッド \(Date\)](../../javascript/reference/setutcdate-method-date-javascript.md)