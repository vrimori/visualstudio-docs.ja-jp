---
title: "setTime メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "setTime"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "SetTime メソッド"
  - "time メソッド"
ms.assetid: 86584748-7219-495b-bf56-e27f5782778c
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# setTime メソッド (Date) (JavaScript)
`Date` オブジェクトの日付と時刻の値を設定します。  
  
## 構文  
  
```  
  
dateObj.setTime(milliseconds)   
```  
  
## パラメーター  
 `dateObj`  
 必須です。  任意の `Date` オブジェクトを指定します。  
  
 *milliseconds*  
 必須です。  グリニッジ標準時の 1970 年 1 月 1 日 0 時 0 分 0 秒から経過したミリ秒数単位の数値を指定します。  
  
## 解説  
 *milliseconds* 引数に負の値を指定すると、1970 年以前の日付になります。  有効な日付の範囲は、1970 年の前後の約 285,616 年です。  
  
 `setTime` メソッドを使用して日付と時刻を設定する場合は、指定する値はタイムゾーンに依存しません。  
  
## 使用例  
 `setTime` メソッドの使用例を次に示します。  
  
```javascript  
function SetTimeTest(newtime){  
   var d, s;                  //Declare variables.  
   d = new Date();            //Create Date object.  
   d.setTime(newtime);        //Set time.  
   s = "Current setting is ";  
   s += d.toUTCString();  
   return(s);                 //Return new setting.  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getTime メソッド \(Date\)](../../javascript/reference/gettime-method-date-javascript.md)