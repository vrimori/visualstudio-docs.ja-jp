---
title: "Date.parse 関数 (JavaScript) | Microsoft Docs"
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
  - "parse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date.parse 関数 [JavaScript]"
  - "parse 関数 [JavaScript]"
ms.assetid: ed737e50-6398-4462-8779-2af3c03f8325
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Date.parse 関数 (JavaScript)
日付を表す文字列を解析し、その日付と 1970 年 1 月 1 日午前 00:00:00 との差を表すミリ秒単位の値を返します。  
  
## 構文  
  
```  
Date.parse(dateVal)   
```  
  
## 解説  
 必須の `dateVal` 引数には、ActiveX オブジェクトまたはその他のオブジェクトから取得した日付または VT\_DATE 値を指定します。  `Date.parse` 関数が解析できる日付文字列については、「[日付と時刻文字列](../../javascript/date-and-time-strings-javascript.md)」を参照してください。  
  
 `Date.parse` 関数は、`dateVal` に指定された日付と 1970 年 1 月 1 日午前 00:00:00 との差をミリ秒単位で表す整数値を返します。  
  
## 使用例  
 `Date.parse` 関数の使用例を次に示します。  
  
```javascript  
var dateString = "November 1, 1997 10:15 AM";  
var mSec = Date.parse(dateString);  
document.write(mSec);  
// Output: 878404500000  
```  
  
## 使用例  
 指定した日付と 1\/1\/1970 の差を返す例を次に示します。  
  
```javascript  
var minMilli = 1000 * 60;  
var hrMilli = minMilli * 60;  
var dyMilli = hrMilli * 24;  
  
var testDate = new Date("June 1, 1990");  
var ms = Date.parse(testDate);  
var days = Math.round(ms / dyMilli);  
  
var dateStr = "";  
dateStr += "There are " + days + " days ";  
dateStr += "between 01/01/1970 and " + testDate;  
document.write(dateStr);  
  
// Output: There are 7456 days between 01/01/1970 and Fri Jun 1 00:00:00 PDT 1990  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [getDate メソッド \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)