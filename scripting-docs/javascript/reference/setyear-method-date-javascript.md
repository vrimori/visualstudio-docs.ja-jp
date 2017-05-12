---
title: "setYear メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "setYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "setYear メソッド"
  - "Year メソッド"
ms.assetid: 36431050-e0ec-45ee-830d-0d7c20e207ea
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# setYear メソッド (Date) (JavaScript)
`Date` オブジェクトの日付の年の部分を設定します。  
  
## 構文  
  
```  
  
dateObj.setYear(numYear)   
```  
  
## パラメーター  
 `dateObj`  
 必須です。  任意の `Date` オブジェクトを指定します。  
  
 `numYear`  
 必須です。  1900 ～ 1999 年の場合は、年から 1900 を引いた数値を指定します。  この範囲に含まれない年の場合は、4 桁の数値を指定します。  
  
## 解説  
 このメソッドは廃止されました。現在、以前のバージョンとの互換性のためだけに残されています。  代わりに、`setFullYear` メソッドを使用してください。  
  
 `Date` オブジェクトに 1997 年を設定するには、**setYear\(97\)** メソッドを実行します。  また、2010 年を設定するには、**setYear\(2010\)** メソッドを実行します。  0 ～ 99 の範囲で年を設定するには、`setFullYear` メソッドを使用します。  
  
> [!NOTE]
>  [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] バージョン 1.0 では、`setYear` メソッドは、年を表す値にかかわらず `numYear` に指定した値に 1900 を加算した結果を使用します。  たとえば、1899 年に設定するときは `numYear` に \-1 を指定し、2000 年に設定するときは `numYear` に 100 を指定します。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [getFullYear メソッド \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear メソッド \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [GetYear メソッド \(Date\)](../../javascript/reference/getyear-method-date-javascript.md)   
 [setFullYear メソッド \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setUTCFullYear メソッド \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)