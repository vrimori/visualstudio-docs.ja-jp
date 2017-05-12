---
title: "getVarDate メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "getVarDate"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date オブジェクト"
  - "getVarDate メソッド"
  - "日付、VT_DATE 形式"
ms.assetid: 561238de-5c91-45a3-b839-a16910d3a1cf
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# getVarDate メソッド (Date) (JavaScript)
`Date` オブジェクトからの VT\_DATE 値を返します。  
  
> [!WARNING]
>  このメソッドは、Internet Explorer でのみサポートされます。  
  
## 構文  
  
```  
  
dateObj.getVarDate()   
```  
  
#### パラメーター  
 必要な `dateObj` 参照は `Date` オブジェクトです。  
  
## 戻り値  
 VT\_DATE 値を返します。  
  
## 解説  
 `getVarDate` メソッドは、JavaScript コードが、COM オブジェクト、ActiveX オブジェクト、または VT\_DATE 形式の日付値を受け入れて返すその他のオブジェクトと対話する場合に使用されます。 これらには、Visual Basic および Visual Basic Scripting Edition \(VBScript\) のオブジェクトが含まれます。 戻り値の実際の形式は、地域の設定によって異なります。  
  
## 必要条件  
 Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準、Internet Explorer 10 標準の各ドキュメント モードでサポートされます。[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリではサポートされていません。 「[バージョン情報](../../javascript/reference/javascript-version-information.md)」を参照してください。  
  
 **適用対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getDate メソッド \(Date\)](../../javascript/reference/getdate-method-date-javascript.md)   
 [Date.parse 関数](../../javascript/reference/date-parse-function-javascript.md)