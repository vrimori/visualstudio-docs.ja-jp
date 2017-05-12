---
title: "getTime メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "getTime"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetTime メソッド"
  - "time メソッド"
ms.assetid: f0da1d4e-337c-497d-9205-093defbc6d3d
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# getTime メソッド (Date) (JavaScript)
時刻値 \(ミリ秒\) を取得します。  
  
## 構文  
  
```  
  
dateObj.getTime()   
```  
  
#### パラメーター  
 `dateObj` 参照は必須で、`Date` オブジェクトを指定します。  
  
## 戻り値  
 1970 年 1 月 1 日午前 00:00:00 と `Date` オブジェクトに格納されている時刻値との差をミリ秒単位で返します。  日付の範囲は、1970 年 1 月 1 日午前 00:00:00 の前後およそ 285,616 年です。  負数は、1970 年以前の日付を示します。  
  
## 解説  
 複数の日付や時刻を使って計算する場合は、1 日、1 時間、1 分間などの時間をミリ秒単位で表す変数を定義しておくことをお勧めします。  次に例を示します。  
  
```javascript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
```  
  
 `getTime` メソッドの使用方法の詳細については、「[日付と時刻の計算 \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)」を参照してください。  
  
## 使用例  
 `getTime` メソッドを使用する方法の例を次に示します。  
  
```javascript  
var minute = 1000 * 60;  
var hour = minute * 60;  
var day = hour * 24;  
  
date = new Date("1/1/2001");  
var time = date.getTime();  
  
document.write(Math.round(time / day) + " days from 1/1/1970 to 1/1/2001");  
  
// Output: 11323 days from 1/1/1970 to 1/1/2001  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [setTime メソッド \(Date\)](../../javascript/reference/settime-method-date-javascript.md)