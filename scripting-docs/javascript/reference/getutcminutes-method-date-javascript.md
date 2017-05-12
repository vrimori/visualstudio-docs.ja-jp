---
title: "getUTCMinutes メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "分"
  - "UTC 時刻、返す"
  - "getUTCMinutes メソッド"
ms.assetid: b6d92543-b285-4e46-8f47-bba36e53fabd
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCMinutes メソッド (Date) (JavaScript)
4 Z 対象時間 \(UTC\) を使用して調整されます `Date` のオブジェクトの分が表示されます。  
  
## 構文  
  
```  
  
dateObj.getUTCMinutes()   
```  
  
#### パラメーター  
 `dateObj` の参照は `Date` の対象です。  
  
## 戻り値  
 0 ~ 59 の間に整数を返します。  ゼロは、時間後に時間は 1 分未満戻されます。  `Date` のオブジェクトが時間を指定せずに作成された場合、既定では UTC 分の値は 0 です。  ただし、別のタイム ゾーンに、異なる場合があります。  
  
## 解説  
 ローカル時間を使用して分の値を取得するには、`getMinutes` メソッドを使用します。  
  
## 使用例  
 `getUTCMinutes` メソッドの使用例を次に示します。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getUTCMinutes());  
  
// Output:   
// 0  
// 5  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 :**Applies To**[Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getMinutes メソッド \(Date\)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [setMinutes メソッド \(Date\)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes メソッド \(Date\)](../../javascript/reference/setutcminutes-method-date-javascript.md)