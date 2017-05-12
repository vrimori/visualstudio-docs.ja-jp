---
title: "getUTCMilliseconds メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ミリ秒"
  - "UTC 時刻、返す"
  - "getUTCMilliseconds メソッド"
ms.assetid: 7491d387-7b6a-40df-89e5-55c64795ef70
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCMilliseconds メソッド (Date) (JavaScript)
4 Z 対象時間 \(UTC\) を使用して調整されます `Date` のオブジェクトのミリ秒\) が表示されます。  
  
## 構文  
  
```  
  
dateObj.getUTCMilliseconds()   
```  
  
#### パラメーター  
 `dateObj` の参照は `Date` の対象です。  
  
## 戻り値  
 0\-999 からまたがることができるミリ秒単位の値を返します。  
  
## 解説  
 ローカル時刻のミリ秒数を取得するには、`getMilliseconds` 方法を使用します。  
  
## 使用例  
 `getUTCMilliseconds` メソッドの使用例を次に示します。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(34);  
document.writedate.getUTCMilliseconds());  
  
// Output:  
// 0   
// 34   
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 :**Applies To**[Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getMilliseconds メソッド \(Date\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [setMilliseconds メソッド \(Date\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds メソッド \(Date\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)