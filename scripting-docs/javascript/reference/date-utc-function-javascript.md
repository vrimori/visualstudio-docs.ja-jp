---
title: "Date.UTC 関数 (JavaScript) | Microsoft Docs"
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
  - "UTC"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "UTC 関数 [JavaScript]"
  - "UTC 日付、返す"
  - "Date.UTC 関数 [JavaScript]"
ms.assetid: c0d67ce1-a47e-4dfd-bbf4-21619c406a0f
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Date.UTC 関数 (JavaScript)
世界協定時刻 \(UTC\) \(つまり GMT\) の 1970 年 1 月 1 日 0 時 0 分 0 秒と、指定した日付との間をミリ秒単位で返します。  
  
## 構文  
  
```  
Date.UTC(year, month, day[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## パラメーター  
 `year`  
 必須です。  日付の年数を必ず 4 桁で指定します。  引数 `year` に 0 ～ 99 の値が指定された場合、`year` は 1900 \+ `year` の値が指定されたと見なされます。  
  
 `month`  
 必須です。  月を表す 0 ～ 11 \(1 ～ 12 月に相当\) の範囲内の整数を指定します。  
  
 `day`  
 必須です。  日を表す 1 ～ 31 の範囲内の整数を指定します。  
  
 `hours`  
 省略可能です。  `minutes` 引数を指定する場合は、この引数を指定する必要があります。  時を表す 0 ～ 23 \(午前 0 時 ～ 午後 11 時に対応\) の範囲内の整数を指定します。  
  
 `minutes`  
 省略可能です。  `seconds` 引数を指定する場合は、この引数を指定する必要があります。  分を表す 0 ～ 59 の範囲内の整数を指定します。  
  
 `seconds`  
 省略可能です。  `milliseconds` 引数を指定する場合は、この引数を指定する必要があります。  秒を表す 0 ～ 59 の範囲内の整数を指定します。  
  
 `ms`  
 省略可能です。  ミリ秒を表す 0 ～ 999 の範囲内の整数を指定します。  
  
## 解説  
 `Date.UTC` 関数は、世界協定時刻での 1970 年 1 月 1 日 0 時 0 分 0 秒と指定した日付の間をミリ秒単位で返します。  この戻り値は、`setTime` メソッドおよび `Date` オブジェクト コンストラクターで使用できます。  引数に有効範囲を超える値や負の値を指定すると、値に応じて格納される他の値が変更されます。  たとえば、150 秒を指定すると、2 分 30 秒として処理されます。  
  
 `Date.UTC` 関数と日付を受け取る `Date` オブジェクトのコンストラクターとの違いは、渡した日付が `Date.UTC` 関数では世界協定時刻 \(UTC\) として扱われ、`Date` オブジェクトのコンストラクターでは現地時間として扱われるという点です。  
  
## 使用例  
 `Date.UTC` 関数の使用例を次に示します。  
  
```javascript  
// Determine the milliseconds per day.  
 var MinMilli = 1000 * 60;  
var HrMilli = MinMilli * 60;  
var DyMilli = HrMilli * 24;  
  
var date = new Date("June 1, 1990");  
var year = date.getFullYear();  
var month = date.getMonth();  
var day = date.getDay();  
  
var newDay = new Date("January 16, 2020");  
var yeartoday = newDay.getUTCFullYear();  
var monthtoday = newDay.getUTCMonth();  
var dayofmonthtoday = newDay.getUTCDate();  
  
// Get the milliseconds since 1/1/1970 UTC.  
var t1 = Date.UTC(year, month - 1, day)  
var t2 = Date.UTC(yeartoday, monthtoday, dayofmonthtoday);  
  
// Determine the difference in days.  
var days = (t2 - t1) / DyMilli;  
  
document.write(days);  
// Output: 10848  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [setTime メソッド \(Date\)](../../javascript/reference/settime-method-date-javascript.md)