---
title: "toLocaleString メソッド (Object) (JavaScript) | Microsoft Docs"
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
  - "toLocaleString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toLocaleString メソッド"
ms.assetid: 0901afcb-126b-4ed7-bd6a-2301d50e2326
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toLocaleString メソッド (Object) (JavaScript)
現在のロケールでの既定の書式を使用して、日付データを文字列に変換します。  
  
## 構文  
  
```  
  
dateObj.toLocaleString()   
```  
  
## 解説  
 `dateObj` は必須で、任意の `Date` のオブジェクトを指定します。  
  
 `toLocaleString` メソッドは、現在のロケールの長い既定形式に日付データを変換し、`String` オブジェクトに書き込んで返します。  
  
-   西暦 1601 から 1999 年の場合、日付はユーザーのコントロール パネルの地域設定に基づいた形式になります。  
  
-   この範囲以外の日付の場合、**toString** メソッドの既定の形式が使用されます。  
  
 たとえば、米国の場合、`toLocaleString` は、1 月 5 日の日付データに対して "01\/05\/96 00:00:00" を返します。  ヨーロッパの場合は、通常、月より日が前になるので、同じ日に対して "05\/01\/96 00:00:00" を返します。  
  
> [!NOTE]
>  `toLocaleString` メソッドは、ユーザーに結果を表示する目的だけで使用してください。この関数の結果はコンピューターによって異なるため、スクリプト内での処理の基準としては使用しないでください。  
  
## 使用例  
 `toLocaleString` メソッドの使用例を次に示します。  
  
```javascript  
function toLocaleStrDemo(){     
   var d, s;                      //Declare variables.  
   d = new Date();                //Create Date object.  
   s = "Current setting is ";  
   s += d.toLocaleString();       //Convert to current locale.  
   return(s);                     //Return converted date  
}  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [Array オブジェクト](../../javascript/reference/array-object-javascript.md)&#124; [Date オブジェクト](../../javascript/reference/date-object-javascript.md)&#124; [Number オブジェクト](../../javascript/reference/number-object-javascript.md)&#124; [Object オブジェクト](../../javascript/reference/object-object-javascript.md)  
  
## 参照  
 [toLocaleDateString メソッド \(Date\)](../../javascript/reference/tolocaledatestring-method-date-javascript.md)