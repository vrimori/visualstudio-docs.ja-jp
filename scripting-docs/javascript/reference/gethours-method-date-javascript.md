---
title: "getHours メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "getHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date オブジェクト"
  - "GetHours メソッド"
  - "Hours メソッド"
ms.assetid: c3936496-a213-4d15-b308-d53926ed310c
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getHours メソッド (Date) (JavaScript)
現地時間で日付の時間の部分を取得します。  
  
## 構文  
  
```  
  
dateObj.getHours()   
```  
  
#### パラメーター  
 `dateObj` 参照は必須で、`Date` オブジェクトを指定します。  
  
## 戻り値  
 Date オブジェクトに格納されている時刻の 0 時からの経過時間を表す 0 ～ 23 の範囲内の整数です。  午前 1:00:00 よりも前の場合は、0 が返されます。  `Date` オブジェクトが時間を指定せずに作成された場合、既定では、時間の値は 0 になります。  
  
## 解説  
 世界協定時刻 \(UTC\) を使用して時の値を取得するには、`getUTCHours` メソッドを使用します。  
  
## 使用例  
 `getHours` メソッドを使用する方法の例を次に示します。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getHours());  
document.write("<br/>");  
  
date.setTime(50000000);  
document.write(date.getHours());  
  
// Output:  
// 0   
// 5  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getUTCHours メソッド \(Date\)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours メソッド \(Date\)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours メソッド \(Date\)](../../javascript/reference/setutchours-method-date-javascript.md)