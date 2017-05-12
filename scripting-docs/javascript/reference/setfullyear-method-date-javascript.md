---
title: "setFullYear メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "setFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Year メソッド"
  - "setFullYear メソッド"
  - "日付、設定"
ms.assetid: 635e4f5a-0210-4c01-8152-b0da4146f6ff
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# setFullYear メソッド (Date) (JavaScript)
ローカル時刻を使用して `Date` のオブジェクトの年を設定します。  
  
## 構文  
  
```  
  
dateObj.setFullYear(numYear[, numMonth[, numDate]])   
```  
  
## パラメーター  
 `dateObj`  
 必須。  任意の `Date` オブジェクトを指定します。  
  
 `numYear`  
 必須。  年の番号。  
  
 `numMonth`  
 省略可能。  月 \(1 年に 0、12 年に 11\) に含まれるベースの番号。  `numDate` を指定すると指定する必要があります。  
  
 `numDate`  
 省略可能。  日の間の数値。  
  
## 解説  
 省略可能な引数を指定せずに **set** で始まる名前の各メソッドを使用した場合、省略した設定の部分には対応する **get** で始まる名前のメソッドで返される値が設定されます。  たとえば `numMonth` の引数がオプションの場合、が指定されていない値が **\[getMonth\]** 方法から返品 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] に使用します。  
  
 また、適切引数の値がカレンダーの範囲内で大きかったりまたは負で、日付ロールフォワードまたは逆に。  
  
 4 Z 対象を使用して年の設定は時間 \(UTC\) を使用します `setUTCFullYear` 方法を調整します。  
  
 オブジェクトの日付でサポートされている年の範囲は 1970 年の前後の約 285,616 年になります。  
  
## 使用例  
 `setFullYear` メソッドの使用例を次に示します。  
  
```javascript  
var date1 = new Date("1/1/2001");  
date1.setFullYear(2007);  
  
var date2 = new Date("1/1/2001");  
date2.setFullYear(2008, 10, 3);   
  
document.write (date1.toLocaleString());  
document.write ("<br />");  
document.write (date2.toLocaleString());  
  
// Output:  
// Monday, January 01, 2007 12:00:00 AM  
// Monday, November 03, 2008 12:00:00 AM  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 :**Applies To**[Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getFullYear メソッド \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear メソッド \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setUTCFullYear メソッド \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)