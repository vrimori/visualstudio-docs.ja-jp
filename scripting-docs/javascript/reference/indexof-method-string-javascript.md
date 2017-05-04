---
title: "indexOf メソッド (String) (JavaScript) | Microsoft Docs"
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
  - "indexOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "indexOf メソッド, string"
  - "string, indexOf メソッド"
ms.assetid: a17372fa-669b-471b-9240-46927a265152
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# indexOf メソッド (String) (JavaScript)
最初に見つかった部分文字列の位置を返します。  
  
## 構文  
  
```  
  
strObj. indexOf(subString[, startIndex])  
```  
  
## パラメーター  
 `strObj`  
 必須。  `String` オブジェクトまたは文字列リテラル。  
  
 `subString`  
 必須。  文字列から検索する部分文字列  
  
 `startIndex`  
 省略可能。  `String` オブジェクトの検索の開始位置を示すインデックス。  省略した場合は、文字列の先頭から検索が開始されます。  
  
## 解説  
 **indexOf** メソッドは `String` オブジェクトの部分文字列の開始位置を返します。  検索文字列が見つからなかった場合は、\-1 が返されます。  
  
 `startindex` に負の値を指定すると、`startindex` は 0 として扱われます。  最も大きいインデックスを超える場合、最も大きいインデックスとして扱われます。  
  
 検索は左から右へと行われます。  この点を除けば、このメソッドは **lastIndexOf** と同じ処理を行います。  
  
## 使用例  
 **indexOf** メソッドの使用例を次に示します。  
  
```javascript  
var str = "original equipment manufacturer";  
  
var s = "equip is at position " + str.indexOf("equip");  
s += "<br />";  
s += "abc is at position " + str.indexOf("abc");  
  
document.write(s);  
  
// Output:  
// equip is at position 9  
// abc is at position -1  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [String オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## 参照  
 [lastIndexOf メソッド \(String\)](../../javascript/reference/lastindexof-method-string-javascript.md)   
 [スクロール、パン、ズームのサンプル アプリ](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)