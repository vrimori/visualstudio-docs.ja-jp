---
title: "setUTCMilliseconds メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "setUTCMilliseconds"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日付, UTC"
  - "ミリ秒"
  - "setUTCMilliseconds メソッド"
  - "UTC 時刻, 設定"
ms.assetid: ed8e4486-d4b2-4b73-836b-dd1d3bb991a0
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# setUTCMilliseconds メソッド (Date) (JavaScript)
`Date` オブジェクトの時刻のミリ秒の部分を世界協定時刻 \(UTC\) で設定します。  
  
## 構文  
  
```  
  
dateObj.setUTCMilliseconds(numMilli)   
```  
  
## パラメーター  
 `dateObj`  
 必須です。  任意の `Date` オブジェクトを指定します。  
  
 `numMilli`  
 必須です。  設定するミリ秒を表す数値を指定します。  
  
## 解説  
 ミリ秒の設定をローカル時間で行うには、`setMilliseconds` メソッドを使用してください。  
  
 `numMilli` 引数に 999 を超える値または負の値を指定すると、値に応じて格納されている秒 \(場合によっては分、時\) の値が変更されます。  
  
## 使用例  
 `setUTCMilliseconds` メソッドの使用例を次に示します。  
  
```javascript  
function SetUTCMSecDemo(nmsec){     
// Create Date object.  
   var d = new Date();             
// Set UTC milliseconds.  
   d.setUTCMilliseconds(nmsec);    
  
   var s = "Current setting is ";  
   s += d.toUTCString();  
   s += " and " + d.getUTCMilliseconds();  
   s += " milliseconds"  
   return(s);  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getMilliseconds メソッド \(Date\)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [getUTCMilliseconds メソッド \(Date\)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setMilliseconds メソッド \(Date\)](../../javascript/reference/setmilliseconds-method-date-javascript.md)