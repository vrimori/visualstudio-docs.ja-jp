---
title: "valueOf メソッド (日付) | Microsoft Docs"
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
ms.assetid: 39a1f96e-14b0-4db2-b53d-cdfd67cbb208
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# valueOf メソッド (日付)
世界協定時刻 \(UTC\) の 1970 年 1 月 1 日 0 時 0 分 0 秒からの経過時間を表すミリ秒単位の時刻値を返します。  
  
## 構文  
  
```  
  
date.valueOf()  
```  
  
#### パラメーター  
 `date` オブジェクトは、Date の任意のインスタンスです。  
  
## 戻り値  
 世界協定時刻 \(UTC\) の 1970 年 1 月 1 日 0 時 0 分 0 秒からの経過時間を表すミリ秒単位の時刻値。  これは、`getTime` と同じ値です。  
  
## 使用例  
 日付を指定した `valueOf` メソッドの使用例を次に示します。  
  
```javascript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
if (myDate.getTime() == myDate.valueOf())  
    document.write("values are the same");  
else  
    document.write("values are different");  
  
// Output: values are the same  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]