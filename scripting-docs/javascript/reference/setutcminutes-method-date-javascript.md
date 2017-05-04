---
title: "setUTCMinutes メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日付, UTC"
  - "分"
  - "setUTCMinutes メソッド"
  - "UTC 時刻, 設定"
ms.assetid: 2415e788-6d28-46dd-a103-0931a1fd1446
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCMinutes メソッド (Date) (JavaScript)
`Date` オブジェクトの時刻の分の部分を世界協定時刻 \(UTC\) で設定します。  
  
## 構文  
  
```  
  
dateObj.setUTCMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## パラメーター  
 `dateObj`  
 必須です。  任意の `Date` オブジェクトを指定します。  
  
 `numMinutes`  
 必須です。  設定する分を表す数値を指定します。  次のいずれかの引数を指定する場合は、この引数を指定する必要があります。  
  
 *numSeconds*  
 省略可能です。  設定する秒を表す数値を指定します。  引数 `numMilli` を指定する場合は、この引数を指定する必要があります。  
  
 `numMilli`  
 省略可能です。  設定するミリ秒を表す数値を指定します。  
  
## 解説  
 省略可能な引数を指定せずに、**set** で始まる名前の各メソッドを使用した場合、省略した設定の部分には対応する **get** で始まる名前のメソッドで返される値が設定されます。  たとえば、*numSeconds* 引数を指定しなかった場合、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] では、`getUTCSeconds` メソッドで返される値が使用されます。  
  
 分の設定を現地時刻で行うには、`setMinutes` メソッドを使用してください。  
  
 引数に有効範囲を超える値や負の値を指定すると、値に応じて格納される他の値が変更されます。  たとえば、格納されている日付が "Jan 5, 1996 00:00:00.00" の場合に、**setUTCMinutes\(70\)** メソッドが呼び出されると、日付は "Jan 5, 1996 01:10:00.00" に変更されます。  
  
 **setUTCHours** メソッドを使用すると、時間、分、秒、ミリ秒を設定できます。  
  
## 使用例  
 `setUTCMinutes` メソッドの使用例を次に示します。  
  
```javascript  
function SetUTCMinutesDemo(nmin, nsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setUTCMinutes(nmin,nsec);  // Set UTC minutes.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                   // Return new setting.  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getMinutes メソッド \(Date\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes メソッド \(Date\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes メソッド \(Date\)](../../javascript/reference/setminutes-method-date-javascript.md)