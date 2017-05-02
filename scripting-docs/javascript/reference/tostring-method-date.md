---
title: "toString メソッド (日付) | Microsoft Docs"
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
ms.assetid: d3037289-d805-409b-8781-045c59a2c404
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# toString メソッド (日付)
日付の文字列表現を返します。  文字列の形式はロケールによって異なります。  米国英語 \(en\-us\) の場合は次のようになります。  
  
 *曜日* *月* *日* *時*:*分*:*秒* *タイム ゾーン* *年*  
  
## 構文  
  
```  
  
date.toString()  
```  
  
## Parameters  
 `date`  
 Required.  文字列として表示する日付を指定します。  
  
## 戻り値  
 日付を表す文字列を返します。  
  
## 使用例  
 日付を指定した `toString` メソッドの使用例を次に示します。  
  
```javascript  
var myDate = new Date();  
myDate.setFullYear(2100, 5, 5);  
var dateString = myDate.toString();  
document.write(dateString);  
  
// Output: <date>  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]