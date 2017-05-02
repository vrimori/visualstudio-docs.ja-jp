---
title: "setUTCDate メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日付, 設定"
  - "日付, UTC"
  - "setUTCDate メソッド"
  - "UTC 日付, 設定"
ms.assetid: e6c3b876-70fe-4103-b197-6c84c078ce10
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# setUTCDate メソッド (Date) (JavaScript)
`Date` オブジェクトに格納されている月の日付の数値を世界協定時刻 \(UTC\) で設定します。  
  
## 構文  
  
```  
  
dateObj.setUTCDate(numDate)   
```  
  
## パラメーター  
 `dateObj`  
 必須です。  任意の `Date` オブジェクトを指定します。  
  
 *numDate*  
 必須です。  月の日付と等しい数値を指定します。  
  
## 解説  
 月の日付を現地時間で設定するには、`setDate` メソッドを使用します。  
  
 **Date**  オブジェクトに格納されている月の日数より大きな値や負の値を引数 *numDate* に指定すると、引数 *numDate* に指定した値から格納されている月の日数を引いた値が日の値に設定されます。  たとえば、1996 年 1 月 5 日の日付が格納されている場合に **setUTCDate\(32\)** を呼び出すと、日付は 1996 年 2 月 1 日に変更されます。  負の値を指定した場合も、同様に処理されます。  
  
 **setUTCFullYear** メソッドを使用すると、年、月、および月の日付を設定できます。  
  
## 使用例  
 `setUTCDate` メソッドの使用例を次に示します。  
  
```javascript  
function SetUTCDateDemo(newdayofmonth){  
   var d = new Date();           // Create Date object.  
   d.setUTCDate(newdayofmonth);  // Set UTC day of month.  
   var s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                    // Return new setting.  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getDate メソッド \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [getUTCDate メソッド \(Date\)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate メソッド \(Date\)](../../javascript/reference/setdate-method-date-javascript.md)