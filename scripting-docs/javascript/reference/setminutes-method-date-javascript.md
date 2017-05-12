---
title: "setMinutes メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "setMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "分"
  - "setMinutes メソッド"
ms.assetid: 34c959cd-cd29-4cee-8e04-9061cf6d42f3
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setMinutes メソッド (Date) (JavaScript)
**Date** オブジェクトの時刻の分の部分を現地時刻で設定します。  
  
## 構文  
  
```  
  
dateObj.setMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## パラメーター  
 `dateObj`  
 必須です。  任意の `Date` オブジェクトを指定します。  
  
 `numMinutes`  
 必須です。  設定する分を表す数値を指定します。  次のいずれかの引数を指定する場合は、この引数を指定する必要があります。  
  
 *numSeconds*  
 省略可能です。  設定する秒を表す数値を指定します。  `numMilli` 引数を使用する場合は、この引数を指定する必要があります。  
  
 `numMilli`  
 省略可能です。  設定するミリ秒を表す数値を指定します。  
  
## 解説  
 省略可能な引数を指定せずに、**set** で始まる名前の各メソッドを使用した場合、省略した設定の部分には対応する **get** で始まる名前のメソッドで返される値が設定されます。  たとえば、*numSeconds* 引数を指定しなかった場合、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] では、`getSeconds` メソッドで返される値が使用されます。  
  
 分の値を世界協定時刻 \(UTC\) で設定するには、`setUTCMinutes` メソッドを使用します。  
  
 引数に有効範囲を超える値や負の値を指定すると、その値に応じて格納されている他の値が変更されます。  たとえば、日付が "Jan 5, 1996 00:00:00" と格納されている場合に **setMinutes\(90\)** メソッドを使用すると、日付は "Jan 5, 1996 01:30:00" に変更されます。負の値を指定した場合も、同様に処理されます。  
  
## 使用例  
 `setMinutes` メソッドの使用例を次に示します。  
  
```javascript  
function SetMinutesDemo(nmin, nsec){  
   var d, s;                     // Declare variables.  
   d = new Date();               // Create Date object.  
   d.setMinutes(nmin, nsec);     // Set minutes.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    // Return new setting.  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getMinutes メソッド \(Date\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes メソッド \(Date\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setUTCMinutes メソッド \(Date\)](../../javascript/reference/setutcminutes-method-date-javascript.md)