---
title: "split メソッド (String) (JavaScript) | Microsoft Docs"
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
  - "split"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "split メソッド"
ms.assetid: 7f093336-c887-4efb-b91f-819b6d18a181
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# split メソッド (String) (JavaScript)
指定した区切り記号を使用して文字列を部分文字列に分割し、配列として返します。  
  
## 構文  
  
```  
  
stringObj.split([separator[, limit]])  
```  
  
## パラメーター  
 `stringObj`  
 必須。  分割する `String` オブジェクトの名前またはリテラル文字列を指定します。  このオブジェクトは、**split** メソッドでは変更されません。  
  
 `separator`  
 省略可能。  文字列を区切る 1 つ以上の文字を表す文字列または **Regular Expression** オブジェクトを指定します。  省略した場合、文字列全体を含む単一要素の配列が返されます。  
  
 `limit`  
 省略可能です。  配列に返される要素の数を制限する値を指定します。  
  
## 戻り値  
 **split** メソッドの結果は、`stringObj` を `separator` の位置で分割してできた文字列の配列です。  `separator` は、配列要素の一部としては返されません。  
  
## 使用例  
 **split** メソッドの使用例を次に示します。  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.split(" ");  
for (var i in ss) {  
    document.write(ss[i]);  
    document.write("<br/>");  
}  
  
// Output:   
// The  
// quick  
// brown  
// fox  
// jumps  
// over  
// the  
// lazy  
// dog.  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [String オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## 参照  
 [concat メソッド \(String\)](../../javascript/reference/concat-method-string-javascript.md)   
 [RegExp オブジェクト](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ja-jp/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [スクロール、パン、ズームのサンプル アプリ](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)