---
title: "getYear メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "getYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "日付、返す (年を)"
  - "GetYear メソッド"
ms.assetid: 0e23e832-acd4-49a9-a175-515d0094f172
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# getYear メソッド (Date) (JavaScript)
`Date` のオブジェクトの年が表示されます。  
  
## 構文  
  
```  
  
dateObj.getYear()   
```  
  
#### パラメーター  
 `dateObj` の参照は `Date` の対象です。  
  
## 戻り値  
 年を返します。  
  
## 解説  
  
> [!IMPORTANT]
>  この方法は使用されなくで、下位互換性のみを目的として提供されます。  代わりに、`getFullYear` メソッドを使用してください。  
  
 次にの [!INCLUDE[jsv1textspecific](../../javascript/reference/includes/jsv1textspecific-md.md)]と [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)]で始まる Internet Explorer のバージョン返される値は 1900 年を保存されている年になります。  たとえば、Date オブジェクトに格納されている年が 1899 年の場合は年数を \-1 で返し、2000 年の場合は、100 を返します。  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)]して [!INCLUDE[jsv3textspecific](../../javascript/reference/includes/jsv3textspecific-md.md)] で、数式は年によって異なります。  1900 年から 1999 年に、返される値は 1900 年を保存されている年に 2 桁の値です。  日付の範囲外に対して、年 4 桁が返されます。  たとえば、1996 年は 96 として返されますが、返されるように 1825 と 2025 が返されます。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 :**Applies To**[Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getFullYear メソッド \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear メソッド \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear メソッド \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear メソッド \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)   
 [setYear メソッド \(Date\)](../../javascript/reference/setyear-method-date-javascript.md)