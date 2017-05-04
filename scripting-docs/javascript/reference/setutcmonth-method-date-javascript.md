---
title: "setUTCMonth メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日付, UTC"
  - "Month メソッド"
  - "setUTCMonth メソッド"
  - "UTC 日付, 設定"
ms.assetid: cdac5f64-c4fd-44cc-ba3a-9a8dd3dd3fad
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCMonth メソッド (Date) (JavaScript)
`Date` オブジェクトの日付の月の部分を世界協定時間 \(UTC\) で設定します。  
  
## 構文  
  
```  
  
dateObj.setUTCMonth(numMonth[, dateVal])   
```  
  
## パラメーター  
 `dateObj`  
 必須です。  任意の `Date` オブジェクトを指定します。  
  
 `numMonth`  
 必須です。  設定する月を表す数値を指定します。  1 月の値は 0 で、2 月以降の値はそれに続く連続した数字です。  
  
 `dateVal`  
 省略可能です。  設定する月の日付と等しい数値を指定します。  省略した場合は、`getUTCDate` メソッドにより返される値が使用されます。  
  
## 解説  
 月の設定を現地時間で行うには、`setMonth` メソッドを使用します。  
  
 引数 `numMonth` に 11 を超える値 \(1 月は 0\) や負の値を指定すると、値に応じて格納されている年の値が変更されます。  たとえば、格納されている日付が "Jan 5, 1996 00:00:00.00" の場合に **setUTCMonth\(14\)** メソッドを使用すると、日付は "Mar 5, 1997 00:00:00.00" に変更されます。  
  
 **setUTCFullYear** メソッドを使用すると、年、月、および月の日付を設定できます。  
  
## 使用例  
 `setUTCMonth` メソッドの使用例を次に示します。  
  
```javascript  
function SetUTCMonthDemo(newmonth){  
   var d, s;                       // Declare variables.  
   d = new Date();                 // Create Date object.  
   d.setUTCMonth(newmonth);        // Set UTC month.  
   s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                      // Return new setting.  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getMonth メソッド \(Date\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth メソッド \(Date\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth メソッド \(Date\)](../../javascript/reference/setmonth-method-date-javascript.md)