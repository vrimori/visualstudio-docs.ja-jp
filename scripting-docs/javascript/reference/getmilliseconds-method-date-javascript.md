---
title: "getMilliseconds メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "getMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ミリ秒"
  - "getMilliseconds メソッド"
ms.assetid: 1b512146-1e8a-44a4-89da-6cc5338d15cb
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getMilliseconds メソッド (Date) (JavaScript)
現地時間で日付のミリ秒の部分を取得します。  
  
## 構文  
  
```  
  
dateObj.getMilliseconds()   
```  
  
#### パラメーター  
 `dateObj` 参照は必須で、`Date` オブジェクトを指定します。  
  
## 戻り値  
 日付のミリ秒の部分を返します。  値の範囲は 0 ～ 999 です。  日付がミリ秒を指定しないで構成されている場合、返される値は 0 です。  
  
## 解説  
 世界協定時刻 \(UTC\) を使用してミリ秒の値を取得するには、`getUTCMilliseconds` メソッドを使用します。  
  
## 使用例  
 **getMilliseconds** メソッドを使用する方法の例を次に示します。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(5);  
document.write(date.getMilliseconds());  
// Output:   
// 0  
// 5  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getUTCMilliseconds メソッド \(Date\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setMilliseconds メソッド \(Date\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds メソッド \(Date\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)