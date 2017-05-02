---
title: "getUTCFullYear メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "getUTCFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getUTCFullYear メソッド"
  - "Date オブジェクト"
  - "UTCFullYear メソッド"
  - "日付、UTC"
  - "UTC 日付、返す"
  - "4 桁で示す年のメソッド"
  - "UTC 日付、取得する"
ms.assetid: f11e5363-ef8a-48dd-9d56-4ee7290c7c48
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# getUTCFullYear メソッド (Date) (JavaScript)
世界協定時刻 \(UTC\) を使用して年を取得します。  
  
## 構文  
  
```  
  
dateObj.getUTCFullYear()   
```  
  
#### パラメーター  
 `dateObj` 参照は必須で、`Date` オブジェクトを指定します。  
  
## 戻り値  
 4 桁の数値として年を返します。  `Date` コンストラクターまたは `setFullYear` で 2 桁として指定した年は 20 世紀であると見なされるため、"5\/14\/12" を指定すると、`getUTCFullYear` は "1912" を返します。  
  
## 解説  
 現地時間を使用して年を取得するには、`getFullYear` メソッドを使用します。  
  
## 使用例  
 `getUTCFullYear` メソッドを使用する方法の例を次に示します。  
  
```javascript  
var date = new Date("1/9/36");  
document.write(date.getUTCFullYear());  
  
// Output: 1936  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getFullYear メソッド \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [setFullYear メソッド \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear メソッド \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)