---
title: "setMilliseconds メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "setMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ミリ秒"
  - "setMilliseconds メソッド"
ms.assetid: 6c398961-130e-4f60-802f-6c30e1ef4de4
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setMilliseconds メソッド (Date) (JavaScript)
`Date` オブジェクトの時刻のミリ秒の部分を現地時刻で設定します。  
  
## 構文  
  
```  
  
dateObj.  
setMilliseconds(  
numMilli  
)   
```  
  
## パラメーター  
 `dateObj`  
 必須です。  任意の `Date` オブジェクトを指定します。  
  
 `numMilli`  
 必須です。  設定するミリ秒を表す数値を指定します。  
  
## 解説  
 ミリ秒の値を世界協定時刻 \(UTC\) で設定するには、`setUTCMilliseconds` メソッドを使用してください。  
  
 `numMilli` 引数に 999 を超える値か負の値を指定すると、値に応じて格納されている秒 \(場合によっては分、時\) の値が変更されます。  
  
## 使用例  
 `setMilliseconds` メソッドの使用例を次に示します。  
  
```javascript  
function SetMSecDemo(nmsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setMilliseconds(nmsec);    // Set milliseconds.  
   s = "Current setting is ";  
   s += d.toLocaleString();  
   s += " and " + d.getMilliseconds();  
   s += " milliseconds";  
   return(s);                   // Return new date setting.  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getMilliseconds メソッド \(Date\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [getUTCMilliseconds メソッド \(Date\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds メソッド \(Date\)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)