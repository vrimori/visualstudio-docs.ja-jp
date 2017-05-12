---
title: "setUTCSeconds メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日付, UTC"
  - "seconds メソッド"
  - "setUTCSeconds メソッド"
  - "UTC 時刻, 設定"
ms.assetid: e035e282-b39d-4d1d-8771-c17542fd6493
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCSeconds メソッド (Date) (JavaScript)
`Date` オブジェクトの時刻の秒の部分を世界協定時刻 \(UTC\) で設定します。  
  
## 構文  
  
```  
  
dateObj.setUTCSeconds(numSeconds[, numMilli])   
```  
  
## パラメーター  
 `dateObj`  
 必須です。  任意の `Date` オブジェクトを指定します。  
  
 *numSeconds*  
 必須です。  設定する秒を表す数値を指定します。  
  
 `numMilli`  
 省略可能です。  設定するミリ秒を表す数値を指定します。  
  
## 解説  
 省略可能な引数を指定せずに、**set** で始まる名前の各メソッドを使用した場合、省略した設定の部分には対応する **get** で始まる名前のメソッドで返される値が設定されます。  たとえば、`numMilli` 引数を指定しなかった場合、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] では、`getUTCMilliseconds` メソッドで返される値が使用されます。  
  
 秒の設定をローカル時間で行うには、`setSeconds` メソッドを使用してください。  
  
 引数に有効範囲を超える値や負の値を指定すると、その値に応じて格納されている他の値が変更されます。  たとえば、格納されている日付が "Jan 5, 1996 00:00:00.00" の場合に **setSeconds\(150\)** メソッドを使用すると、日付は "Jan 5, 1996 00:02:30.00" に変更されます。  
  
 **setUTCHours** メソッドを使用すると、時間、分、秒、ミリ秒を設定できます。  
  
## 使用例  
 `setUTCSeconds` メソッドの使用例を次に示します。  
  
```javascript  
function SetUTCSecondsDemo(nsec){  
// Create Date object.  
    var d = new Date();       
// Set UTC seconds.  
    d.setUTCSeconds(nsec);    
    var s = "Current setting is ";  
    s += d.toUTCString();  
// Return new setting.  
    return(s);                
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getSeconds メソッド \(Date\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds メソッド \(Date\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds メソッド \(Date\)](../../javascript/reference/setseconds-method-date-javascript.md)