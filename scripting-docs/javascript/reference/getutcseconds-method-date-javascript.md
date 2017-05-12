---
title: "getUTCSeconds メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "UTC 時刻、返す"
  - "seconds メソッド"
  - "getUTCSeconds メソッド"
ms.assetid: 2d8ea7dc-79f8-4a9b-b2ab-732db2bcd5fd
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCSeconds メソッド (Date) (JavaScript)
4 Z 対象時間 \(UTC\) を使用して調整されます `Date` のオブジェクトの秒が表示されます。  
  
## 構文  
  
```  
  
dateObj.getUTCSeconds()   
```  
  
#### パラメーター  
 `dateObj` の参照は `Date` の対象です。  
  
## 戻り値  
 0 ~ 59 の間に整数を返します。  ゼロと時間が分な期限内に 1 秒未満の場合になります。  `Date` のオブジェクトが時間を指定せずに作成された場合、既定では UTC の秒の値は 0 です。  
  
## 解説  
 ローカル時間を使用して秒の値を取得するには、`getSeconds` メソッドを使用します。  
  
## 使用例  
 `getUTCSeconds` メソッドを使用する方法の例を次に示します。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date. getUTCSeconds());  
  
// Output: 0  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 :**Applies To**[Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getSeconds メソッド \(Date\)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [setSeconds メソッド \(Date\)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds メソッド \(Date\)](../../javascript/reference/setutcseconds-method-date-javascript.md)