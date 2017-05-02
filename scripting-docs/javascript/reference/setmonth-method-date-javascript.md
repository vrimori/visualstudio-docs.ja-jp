---
title: "setMonth メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "setMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Month メソッド"
  - "setMonth メソッド"
ms.assetid: 4f5be295-d536-46c0-b3a4-ad06457efe82
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# setMonth メソッド (Date) (JavaScript)
`Date` オブジェクトの日付の月の部分を現地時刻で設定します。  
  
## 構文  
  
```  
  
dateObj. setMonth(numMonth[, dateVal])   
```  
  
## パラメーター  
 `dateObj`  
 必須です。  任意の `Date` オブジェクトを指定します。  
  
 `numMonth`  
 必須です。  設定する月を表す数値を指定します。  1 月の値は 0 で、2 月以降の値はそれに続く連続した数字です。  
  
 `dateVal`  
 省略可能です。  設定する月の日付と等しい数値を指定します。  この値を省略した場合は、`getDate` メソッドにより返される値が使用されます。  
  
## 解説  
 世界協定時刻 \(UTC\) を使用して月の値を設定するには、`setUTCMonth` メソッドを使用します。  
  
 `numMonth` に 11 を超える値 \(1 月は 0\) または負数を指定すると、値に応じて格納されている年の値が変更されます。  たとえば、日付が "Jan 5, 1996" と格納されている場合に **setMonth\(14\)** メソッドを呼び出すと、日付は "Mar 5, 1997" に変更されます。  
  
 **setFullYear** メソッドを使用すると、年、月、および日を設定できます。  
  
## 使用例  
 `setMonth` メソッドの使用例を次に示します。  
  
```javascript  
date = new Date('1/1/1990');  
date.setMonth(14);  
document.write(date);  
  
// Output: Fri Mar 1 00:00:00 PST 1991  
// Note that the time zone corresponds to the time zone on the local computer.  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getMonth メソッド \(Date\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth メソッド \(Date\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setUTCMonth メソッド \(Date\)](../../javascript/reference/setutcmonth-method-date-javascript.md)