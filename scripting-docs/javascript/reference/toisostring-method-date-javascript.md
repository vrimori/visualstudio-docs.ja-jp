---
title: "toISOString メソッド (Date) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toISOString メソッド [JavaScript]"
ms.assetid: 58577d8f-3ae8-4887-8687-26233ea79ff6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# toISOString メソッド (Date) (JavaScript)
日付を ISO 形式の文字列値として返します。  
  
## 構文  
  
```javascript  
  
objDate.toISOString()  
```  
  
## 戻り値  
 国際標準化機構 \(ISO\) 形式の日付の文字列表現。  
  
## 例外  
 `objDate` に有効な日付が含まれていない場合は、`RangeError` 例外がスローされます。  
  
## 解説  
 ISO 形式は、ISO 8601 形式の簡略化バージョンです。  詳細については、「[日付と時刻文字列](../../javascript/date-and-time-strings-javascript.md)」を参照してください。  
  
 タイム ゾーンは常に UTC で、出力ではサフィックスの Z で示されます。  
  
## 使用例  
 `toISOString` メソッドの使用例を次に示します。  
  
```javascript  
var dt = new Date("30 July 2010 15:05 UTC");  
document.write(dt.toISOString());  
document.write("<br />");  
document.write(dt.toUTCString());  
  
// Output:  
//  2010-07-30T15:05:00.000Z  
//  Fri, 30 Jul 2010 15:05:00 UTC  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## 参照  
 [Date オブジェクト](../../javascript/reference/date-object-javascript.md)   
 [日付と時刻文字列](../../javascript/date-and-time-strings-javascript.md)