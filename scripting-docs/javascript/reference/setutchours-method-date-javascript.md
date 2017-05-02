---
title: "setUTCHours メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日付, UTC"
  - "setUTCHours メソッド"
  - "UTC 時刻, 設定"
ms.assetid: 257e36fd-fb06-4a4d-8634-d66a020a1511
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# setUTCHours メソッド (Date) (JavaScript)
`Date` オブジェクトの時刻の時の部分を世界協定時刻 \(UTC\) で設定します。  
  
## 構文  
  
```  
  
dateObj.setUTCHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## パラメーター  
 `dateObj`  
 必須です。  任意の `Date` オブジェクトを指定します。  
  
 `numHours`  
 必須です。  設定する時を表す数値を指定します。  
  
 `numMin`  
 省略可能です。  設定する分を表す数値を指定します。  `numSec` または `numMilli` を使用する場合は、この引数を指定する必要があります。  
  
 `numSec`  
 省略可能です。  設定する秒を表す数値を指定します。  `numMilli` 引数を使用する場合は、この引数を指定する必要があります。  
  
 `numMilli`  
 省略可能です。  設定するミリ秒を表す数値を指定します。  
  
## 解説  
 省略可能な引数を指定せずに、**set** で始まる名前の各メソッドを使用した場合、省略した設定の部分には対応する **get** で始まる名前のメソッドで返される値が設定されます。  たとえば、`numMin` 引数を指定しなかった場合、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] では、`getUTCMinutes` メソッドで返される値が使用されます。  
  
 時の設定を現地時刻で行うには、`setHours` メソッドを使用してください。  
  
 引数に有効範囲を超える値や負の値を指定すると、値に応じて格納される他の値が変更されます。  たとえば、格納されている日付が "Jan 5, 1996 00:00:00.00" の場合に **setUTCHours\(30\)** メソッドが呼び出されると、日付は "Jan 6, 1996 06:00:00.00" に変更されます。  
  
## 使用例  
 `setUTCHours` メソッドの使用例を次に示します。  
  
```javascript  
function SetUTCHoursDemo(nhr, nmin, nsec){     
   var d, s;                        // Declare variables.  
   d = new Date();                  // Create Date object.  
   d.setUTCHours(nhr, nmin, nsec);  // Set UTC hours, minutes, seconds.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                       // Return new setting.  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getHours メソッド \(Date\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [getUTCHours メソッド \(Date\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours メソッド \(Date\)](../../javascript/reference/sethours-method-date-javascript.md)