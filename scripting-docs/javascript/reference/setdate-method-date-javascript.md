---
title: "setDate メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "setDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "setDate メソッド"
  - "日付、設定"
ms.assetid: a84b9b01-a6d0-489f-8a13-e7af9e9630b2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# setDate メソッド (Date) (JavaScript)
ローカル時刻を使用して `Date` のオブジェクトの数値日の月の値を設定します。  
  
## 構文  
  
```  
  
dateObj.setDate(numDate)   
```  
  
## パラメーター  
 `dateObj`  
 必須。  任意の `Date` オブジェクトを指定します。  
  
 `numDate`  
 必須。  設定する月の日付と等しい数値を指定します。  
  
## 解説  
 4 Z 対象を使用して日の月の値を設定すると、時間 \(UTC\) を使用します `setUTCDate` 方法を調整します。  
  
 `numDate` の値を月の日数、この日付は以降の月、または年にロールのオーバーします。  たとえば `setDate(32)` 保存されている日付が 1 年 3 月 5 日で、1996 年 1、1996 年から 2 年 12 月 1 日までの日付の変更と呼ばれます。  `numDate` が負の場合、日付よりも前の月または年にロールバックされます。  たとえば `setDate(-32)` 保存されている日付が 1 年 3 月 5 日で、1996 年 1、1995 年から 11 年 12 月 29 日までの日付の変更と呼ばれます。  
  
 [setFullYear メソッド \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md) が年、月、日を設定するために使用できます。  
  
## 使用例  
 `setDate` メソッドを使用する方法の例を次に示します。  
  
```javascript  
var date = new Date("12/15/1990");  
date.setDate(30);  
document.write(date);  
  
// Output (for the PST time zone): Sun Dec 30 00:00:00 PST 1990  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 :**Applies To**[Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getDate メソッド \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [setFullYear メソッド \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setMonth メソッド \(Date\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCDate メソッド \(Date\)](../../javascript/reference/setutcdate-method-date-javascript.md)