---
title: "getSeconds メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "getSeconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "seconds メソッド"
  - "GetSeconds メソッド"
ms.assetid: 97b10674-af0b-4681-a846-38f972196501
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# getSeconds メソッド (Date) (JavaScript)
ローカル時刻を使用して `Date` のオブジェクトの秒 \(取得されます。  
  
## 構文  
  
```  
  
dateObj.getSeconds()   
```  
  
#### パラメーター  
 `dateObj` の参照は `Date` の対象です。  
  
## 戻り値  
 0 ~ 59 の間に整数を返します。  ゼロと時間が分な期限内に 1 秒未満の場合になります。  `Date` のオブジェクトが時間を指定せずに作成された場合、既定では秒の値は 0 です。  
  
## 解説  
 取得するには値が 4 Z 対象を使用して時間 \(UTC\) を調整する秒、`getUTCSeconds` 方法を使用します。  
  
## 使用例  
 `getSeconds` メソッドを使用する方法の例を次に示します。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getSeconds());  
document.write("<br/>");  
  
date.setSeconds(5);  
document.write(date.getSeconds());  
  
// Output:  
// 0  
// 5  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 :**に適用されます。**[Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getUTCSeconds メソッド \(Date\)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds メソッド \(Date\)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds メソッド \(Date\)](../../javascript/reference/setutcseconds-method-date-javascript.md)