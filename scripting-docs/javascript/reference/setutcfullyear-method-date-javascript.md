---
title: "setUTCFullYear メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日付, UTC"
  - "setUTCFullYear メソッド"
  - "UTC 日付, 設定"
ms.assetid: e6c51b49-0149-4f9a-aa74-c73c0306f98e
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCFullYear メソッド (Date) (JavaScript)
`Date` オブジェクトの日付の年の部分を世界協定時刻 \(UTC\) で設定します。  
  
## 構文  
  
```  
  
dateObj.setUTCFullYear(numYear[, numMonth[, numDate]])   
```  
  
## パラメーター  
 `dateObj`  
 必須です。  任意の `Date` オブジェクトを指定します。  
  
 `numYear`  
 必須です。  年を表す数値を指定します。  
  
 `numMonth`  
 省略可能です。  設定する月を表す数値を指定します。  1 月の値は 0 で、2 月以降の値はそれに続く連続した数字です。  *numDate* 引数を指定する場合は、この引数を指定する必要があります。  
  
 *numDate*  
 省略可能です。  月の日付と等しい数値を指定します。  
  
## 解説  
 省略可能な引数を指定せずに、**set** で始まる名前の各メソッドを使用した場合、省略した設定の部分には対応する **get** で始まる名前のメソッドで返される値が設定されます。  たとえば、`numMonth` 引数を指定しなかった場合、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] では、`getUTCMonth` メソッドで返される値が使用されます。  
  
 引数に有効範囲を超える値や負の値を指定すると、値に応じて格納されている他の値が変更されます。  
  
 年の設定をローカル時間で行うには、`setFullYear` メソッドを使用してください。  
  
 `Date` オブジェクトでサポートされている年の範囲は、1970 年の前後の約 285,616 年です。  
  
## 使用例  
 `setUTCFullYear` メソッドの使用例を次に示します。  
  
```javascript  
var dtFirst = new Date();  
dtFirst.setUTCFullYear(2007);  
  
var dtSecond = new Date();  
// 10 is the value for November.   
dtSecond.setUTCFullYear(2008, 10, 3);   
  
document.write (dtFirst.toUTCString());  
document.write ("<br />");  
document.write (dtSecond.toUTCString());  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getFullYear メソッド \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear メソッド \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear メソッド \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)