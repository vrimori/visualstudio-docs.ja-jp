---
title: "Date.now 関数 (JavaScript) | Microsoft Docs"
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
  - "now メソッド"
ms.assetid: 41beda89-1a40-4fb1-88b0-38c090af739b
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Date.now 関数 (JavaScript)
現在の日付と時刻を取得します。  
  
## 構文  
  
```  
  
Date.now()  
```  
  
## 戻り値  
 1970 年 1 月 1 日 0 時 0 分 0 秒と現在の日付と時刻の間のミリ秒単位。  
  
## 解説  
 [getTime メソッド](../../javascript/reference/gettime-method-date-javascript.md)は、1970 年 1 月 1 日と指定した日付との間をミリ秒単位で返します。  
  
 経過時間の計算方法および日付の比較方法の詳細については、「[日付と時刻の計算 \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)」を参照してください。  
  
## 使用例  
 `now` メソッドの使用例を次に示します。  
  
```javascript  
var start = Date.now();  
var response = prompt("What is your name?", "");  
var end = Date.now();  
var elapsed = (end - start) / 1000;  
document.write("You took " + elapsed + " seconds" + " to type: " + response);  
  
// Output:  
// You took <seconds> seconds to type: <name>  
```  
  
## 必要条件  
 Internet Explorer 9 より前のインストールされているバージョンではサポートされていません。  ただし、Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準、および Internet Explorer 10 標準の各ドキュメント モードではサポートされます。  さらに、[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリでもサポートされます。  
  
## 参照  
 [getTime メソッド \(Date\)](../../javascript/reference/gettime-method-date-javascript.md)   
 [Date オブジェクト](../../javascript/reference/date-object-javascript.md)   
 [日付と時刻の計算 \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)   
 [JavaScript メソッド](../../javascript/reference/javascript-methods.md)