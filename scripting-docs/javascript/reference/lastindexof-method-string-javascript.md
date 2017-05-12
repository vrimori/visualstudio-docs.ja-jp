---
title: "lastIndexOf メソッド (String) (JavaScript) | Microsoft Docs"
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
  - "lastIndexOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "lastIndexOf メソッド、string"
  - "string、lastIndexOf メソッド"
ms.assetid: 1ed36ccd-0f0b-4f16-be45-0567207670af
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# lastIndexOf メソッド (String) (JavaScript)
文字列における部分文字列の最後のオカレンスを返します。  
  
## 構文  
  
```  
  
strObj.lastIndexOf(substring[, startindex])  
```  
  
## パラメーター  
 `strObj`  
 必須です。  `String` オブジェクトまたはリテラル文字列。  
  
 `substring`  
 必須です。  検索対象の部分文字列。  
  
 `startindex`  
 省略可能です。  検索の開始位置を示すインデックス。  省略した場合は、文字列の末尾から検索が開始されます。  
  
## 解説  
 **lastIndexOf** メソッドの戻り値は、`String` オブジェクト内で見つかった検索文字列の先頭位置を示す整数値です。  検索文字列が見つからなかった場合は、\-1 が返されます。  
  
 `startindex` に負の値を指定すると、`startindex` は 0 として扱われます。  また、最大位置番号より大きい値を指定した場合は、最大位置番号として処理されます。  
  
 検索は文字列の最後の文字から実行されます。  この点を除けば、このメソッドは **indexOf** と同じ処理を行います。  
  
 **lastIndexOf** メソッドの使用例を次に示します。  
  
```javascript  
var str = "time, time";  
  
var s = "";  
s += "time is at position " + str.lastIndexOf("time");  
s += "<br />";  
s += "abc is at position " + str.lastIndexOf("abc");  
  
document.write(s);  
  
// Output:  
// time is at position 6  
// abc is at position -1  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [String オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## 参照  
 [indexOf メソッド \(String\)](../../javascript/reference/indexof-method-string-javascript.md)