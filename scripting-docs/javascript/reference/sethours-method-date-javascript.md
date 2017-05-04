---
title: "setHours メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "setHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日付, 設定"
  - "時間"
  - "setHours メソッド"
ms.assetid: 460f742d-f8d2-4874-9d07-2fb969fef066
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# setHours メソッド (Date) (JavaScript)
`Date` オブジェクトの時刻の時の部分を現地時刻で設定します。  
  
## 構文  
  
```  
  
dateObj.setHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## パラメーター  
 `dateObj`  
 必須です。  任意の `Date` オブジェクトを指定します。  
  
 `numHours`  
 必須です。  設定する時を表す数値を指定します。  
  
 `numMin`  
 省略可能です。  設定する分を表す数値を指定します。  次のいずれかの引数を指定する場合は、この引数を指定する必要があります。  
  
 `numSec`  
 省略可能です。  設定する秒を表す数値を指定します。  次の引数を使用する場合は、この引数を指定する必要があります。  
  
 `numMilli`  
 省略可能です。  設定するミリ秒を表す数値を指定します。  
  
## 解説  
 省略可能な引数を指定せずに、**set** で始まる名前の各メソッドを使用した場合、省略した設定の部分には対応する **get** で始まる名前のメソッドで返される値が設定されます。  たとえば、`numMinutes` 引数を指定しなかった場合、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] では、`getMinutes` メソッドで返される値が使用されます。  
  
 世界協定時刻 \(UTC\) を使用して時の値を設定するには、`setUTCHours` メソッドを使用します。  
  
 引数に有効範囲を超える値や負の値を指定すると、その値に応じて格納されている他の値が変更されます。  たとえば、日付が "Jan 5, 1996 00:00:00" と格納されている場合に **setHours\(30\)** メソッドを使用すると、日付は "Jan 6, 1996 06:00:00" に変更されます。負の値を指定した場合も、同様に処理されます。  
  
## 使用例  
 `setHours` メソッドの使用例を次に示します。  
  
```javascript  
function SetHoursDemo(nhr, nmin, nsec){  
   var d, s;                     //Declare variables.  
   d = new Date();               //Create Date object.  
   d.setHours(nhr, nmin, nsec);  //Set hours, minutes, & seconds.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    //Return new date setting.  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getHours メソッド \(Date\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [getUTCHours メソッド \(Date\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setUTCHours メソッド \(Date\)](../../javascript/reference/setutchours-method-date-javascript.md)