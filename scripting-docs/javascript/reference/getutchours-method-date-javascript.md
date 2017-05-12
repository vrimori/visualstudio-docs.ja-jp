---
title: "getUTCHours メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCHours"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "時間"
  - "UTC 時刻、返す"
  - "getUTCHours メソッド"
ms.assetid: 7c9825dd-4b3a-4614-8e09-f40df123b630
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCHours メソッド (Date) (JavaScript)
4 Z 対象時間 \(UTC\) を使用して調整されます `Date` のオブジェクトの時間の値が表示されます。  
  
## 構文  
  
```  
  
dateObj.getUTCHours()   
```  
  
#### パラメーター  
 `dateObj` の参照は `Date` の対象です。  
  
## 戻り値  
 現在の日付の時間数を示す 0 ~ 23 の間に整数を返します。  ゼロと時間が 1:00 より前にある返品されます: 00 A.M  `Date` のオブジェクトが時間を指定せずに作成された場合、既定では時間は UTC 時刻の 0 です。  この時刻は別のタイム ゾーンで非ゼロである場合があります。  
  
## 解説  
 ローカル時間での 0 時からの時単位の経過時間を取得するには、`getHours` メソッドを使用します。  
  
## 使用例  
 `getUTCHours` メソッドの使用例を次に示します。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCHours());  
document.write("<br/>");  
  
var date2 = new Date("1/1/2001 11:22:33");  
document.write(datee.getUTCHours());  
  
// Output (in the PST time zone):  
// 8  
// 19  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 :**Applies To**[Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getHours メソッド \(Date\)](../../javascript/reference/gethours-method-date-javascript.md)   
 [setHours メソッド \(Date\)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours メソッド \(Date\)](../../javascript/reference/setutchours-method-date-javascript.md)