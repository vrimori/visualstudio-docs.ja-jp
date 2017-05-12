---
title: "getFullYear メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "getFullYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日付、返す (年を)"
  - "Date オブジェクト"
  - "getFullYear メソッド"
ms.assetid: f9ec1262-02e9-4791-90b5-48f33b1dc4bc
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# getFullYear メソッド (Date) (JavaScript)
年の値を現地時間で取得します。  
  
## 構文  
  
```  
  
dateObj.getFullYear()   
```  
  
#### パラメーター  
 `dateObj` 参照は必須で、`Date` オブジェクトを指定します。  
  
## 戻り値  
 年 \(4 桁の数値\)。  たとえば、1976 年の場合は "1976" を返します。  `Date` コンストラクターまたは `setFullYear` で 2 桁として指定した年は 20 世紀であると見なされるため、"5\/14\/12" を指定すると、`getFullYear` は "1912" を返します。  
  
## 解説  
 世界協定時刻 \(UTC\) を使用して年を取得するには、`getUTCFullYear` メソッドを使用します。  
  
## 使用例  
 **getFullYear** メソッドの使用例を次に示します。  
  
```javascript  
var date = new Date("1/1/01");  
document.write(date.getFullYear());  
  
// Output: 1901  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getUTCFullYear メソッド \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear メソッド \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear メソッド \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)