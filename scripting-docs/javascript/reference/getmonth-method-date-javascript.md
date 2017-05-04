---
title: "getMonth メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "getMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date オブジェクト"
  - "日付、月の値"
  - "Month メソッド"
  - "GetMonth メソッド"
ms.assetid: c20dd8ba-1d78-42f1-8717-ed3dfd2362dd
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# getMonth メソッド (Date) (JavaScript)
月の値を現地時間で取得します。  
  
## 構文  
  
```  
  
dateObj.getMonth()   
```  
  
#### パラメーター  
 `dateObj` 参照は必須で、`Date` オブジェクトを指定します。  
  
## 戻り値  
 `getMonth` メソッドは、月を表す 0 \(1 月\) ～ 11 \(12 月\) の範囲内の整数を返します。  "Jan 5, 1996" を使って構築されている `Date` の場合、`getMonth` は 0 を返します。  
  
## 解説  
 世界協定時刻 \(UTC\) を使用して月の値を取得するには、`getUTCMonth` メソッドを使用します。  
  
## 使用例  
 `getMonth` メソッドを使用する方法の例を次に示します。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMonth());  
  
// Output: 0  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getUTCMonth メソッド \(Date\)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth メソッド \(Date\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCMonth メソッド \(Date\)](../../javascript/reference/setutcmonth-method-date-javascript.md)