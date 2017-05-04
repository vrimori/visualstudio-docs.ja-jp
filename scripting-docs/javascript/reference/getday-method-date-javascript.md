---
title: "getDay メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "getDay"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetDay メソッド"
  - "Date オブジェクト"
  - "日付、週の曜日を返す"
ms.assetid: 27be7168-3dce-41c9-ae69-6280b7984c2e
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# getDay メソッド (Date) (JavaScript)
曜日を現地時刻で取得します。  
  
## 構文  
  
```  
  
dateObj. getDay()   
```  
  
#### パラメーター  
 `dateObj` 参照は必須で、`Date` オブジェクトを指定します。  
  
## 戻り値  
 曜日を表す 0 \(日曜日\) ～ 6 \(土曜日\) の整数を返します。  
  
## 解説  
 世界協定時刻 \(UTC\) を使用して曜日を取得するには、`getUTCDay` メソッドを使用します。  
  
 `getDay` メソッドを使用する方法の例を次に示します。  
  
```javascript  
var date = new Date("Saturday, February 9, 2008");  
day = date.getDay();  
document.write(day);  
  
// Output: 6  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getUTCDay メソッド \(Date\)](../../javascript/reference/getutcday-method-date-javascript.md)