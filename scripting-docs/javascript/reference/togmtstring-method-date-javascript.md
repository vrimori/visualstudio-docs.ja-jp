---
title: "toGMTString メソッド (Date) (JavaScript) | Microsoft Docs"
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
  - "toGMTString"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "toGMTString メソッド"
ms.assetid: 9dc1e722-5722-4b8c-a213-a2650f55f207
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# toGMTString メソッド (Date) (JavaScript)
グリニッジ標準時 \(GMT\) を使用して日付データを文字列に変換します。  
  
## 構文  
  
```  
  
dateObj.toGMTString()   
```  
  
## 解説  
 必須の `dateObj` 参照には、任意の `Date` オブジェクトを指定します。  
  
 `toGMTString` メソッドは廃止されました。現在、以前のバージョンとの互換性のためだけに残されています。  代わりに、`toUTCString` メソッドの使用をお勧めします。  
  
 `toGMTString` メソッドは、日付を GMT 規約に基づいた表記に変換し、`String` オブジェクトに格納して返します。  戻り値の書式は、"05 Jan 1996 00:00:00 GMT" です。  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [Date オブジェクト](../../javascript/reference/date-object-javascript.md)  
  
## 参照  
 [toUTCString メソッド \(Date\)](../../javascript/reference/toutcstring-method-date-javascript.md)