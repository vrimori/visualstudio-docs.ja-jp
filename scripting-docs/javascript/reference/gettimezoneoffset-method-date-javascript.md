---
title: "getTimezoneOffset メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "getTimeZoneOffset"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "getTimezoneOffset メソッド"
  - "タイム ゾーン [Visual Studio]"
ms.assetid: 58ee22b0-4688-45bd-a337-cc23119b09ce
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# getTimezoneOffset メソッド (Date) (JavaScript)
ローカル コンピューターの時刻と世界協定時刻 \(UTC\) との差を分単位の値で取得します。  
  
## 構文  
  
```  
  
dateObj.getTimezoneOffset()   
```  
  
#### パラメーター  
 `dateObj` 参照は必須で、`Date` オブジェクトを指定します。  
  
## 戻り値  
 現在のコンピューター \(クライアント コンピューター、またはメソッドがサーバー スクリプトから呼び出された場合はサーバー コンピューター\) の時刻と UTC の時刻との差を分数で返します。  現在のコンピューターの現地時刻が UTC より遅い場合 \(太平夏時間など\) は正の値に、UTC より早い場合 \(日本時間など\) は負の値になります。  たとえば、ニューヨークのサーバーが、12 月 1 日にロサンゼルスのクライアントからのアクセスを受けたとします。その場合、`getTimezoneOffset` は、クライアント上で実行されると 480 を返し、サーバー上で実行されると 300 を返します。  
  
## 解説  
  
## 使用例  
 `getTimezoneOffset` メソッドを使用する方法の例を次に示します。  
  
```javascript  
var date =  new Date();  
var minutes = date.getTimezoneOffset();  
  
if (minutes < 0)  
    document.write(minutes / 60 + " hours after UTC");  
else  
    document.write(minutes / 60 + " hours before UTC");  
  
// Output (for example, where local time is PST):   
7 hours before UTC  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getTime メソッド \(Date\)](../../javascript/reference/gettime-method-date-javascript.md)