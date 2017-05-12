---
title: "getUTCMonth メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCMonth"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日付、UTC"
  - "UTC 日付、返す"
  - "Month メソッド"
  - "getUTCMonth メソッド"
ms.assetid: eabae139-4da0-4e4a-a4cb-608e6375fc9e
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCMonth メソッド (Date) (JavaScript)
4 Z 対象時間 \(UTC\) を使用して調整されます `Date` のオブジェクトの月が表示されます。  
  
## 構文  
  
```  
  
dateObj.getUTCMonth()   
```  
  
#### パラメーター  
 `dateObj` の参照は `Date` の対象です。  
  
## 戻り値  
 0 \(1 ~ 11\) との間に整数を返します \(月 12\)。  
  
## 解説  
 ローカル時間を使用して月の値を取得するには、**getMonth** メソッドを使用します。  
  
## 使用例  
 `getUTCMonth` メソッドを使用する方法の例を次に示します。  
  
```javascript  
var date = new Date("2/2/2002");  
document.write(date.getUTCMonth());  
  
// Output: 1  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 :**Applies To**[Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getMonth メソッド \(Date\)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [setMonth メソッド \(Date\)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCMonth メソッド \(Date\)](../../javascript/reference/setutcmonth-method-date-javascript.md)