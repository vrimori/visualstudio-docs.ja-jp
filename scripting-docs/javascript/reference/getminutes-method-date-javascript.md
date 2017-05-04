---
title: "getMinutes メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "getMinutes"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetMinutes メソッド"
  - "minutes メソッド"
ms.assetid: d4139b5d-04e1-474c-9a83-e9d40597243a
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getMinutes メソッド (Date) (JavaScript)
現地時間で `Date` オブジェクトの分の部分を取得定します。  
  
## 構文  
  
```  
  
dateObj.getMinutes()   
```  
  
#### パラメーター  
 `dateObj` 参照は必須で、`Date` オブジェクトを指定します。  
  
## 戻り値  
 0 ～ 59 の整数値を返します。  1 時間のうちの最初の 1 分を経過していない場合はゼロが返されます。  `Date` オブジェクトが時間を指定せずに作成された場合、既定では、分の値は 0 になります。  
  
## 解説  
 世界協定時刻 \(UTC\) で分の値を取得するには、`getUTCMinutes` メソッドを使用します。  
  
## 使用例  
 `getMinutes` メソッドを使用する方法の例を次に示します。  
  
```javascript  
var date = new Date("1/1/2001");  
document.write(date.getMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getMinutes());  
  
// Output:  
// 0  
// 5  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getUTCMinutes メソッド \(Date\)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes メソッド \(Date\)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes メソッド \(Date\)](../../javascript/reference/setutcminutes-method-date-javascript.md)