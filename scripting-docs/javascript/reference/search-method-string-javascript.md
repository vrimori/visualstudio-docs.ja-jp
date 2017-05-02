---
title: "search メソッド (String) (JavaScript) | Microsoft Docs"
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
  - "search"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "search メソッド"
ms.assetid: 1cae0fbc-3319-4327-ba4e-d5fa2c4a9ba0
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# search メソッド (String) (JavaScript)
正規表現検索に一致する、最初の部分文字列を検索します。  
  
## 構文  
  
```  
  
stringObj.search(rgExp)   
```  
  
## パラメーター  
 `stringObj`  
 必須です。  検索対象とする `String` オブジェクトの名前またはリテラル文字列を指定します。  
  
 `rgExp`  
 必須です。  検索に使用する正規表現のパターンと適用できるフラグを格納した **Regular Expression** オブジェクトのインスタンスです。  
  
## 戻り値  
 一致する文字列が見つかった場合、**search** メソッドは、最初に見つかった文字列の、先頭からのオフセットを示す整数値を返します。  一致する文字列が見つからなかった場合は、\-1 を返します。  
  
## 解説  
 また、`i` のフラグを設定し、検索で大文字小文字を区別することもできます。  
  
## 使用例  
 **search** メソッドの使用例を次に示します。  
  
```javascript  
var src = "is but a Dream within a dream";  
var re = /dream/;  
var pos = src.search(re);  
document.write(pos);  
document.write("<br/>");  
  
re = /dream/i;  
pos = src.search(re);  
document.write(pos);  
  
// Output:   
// 24   
// 9  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [String オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## 参照  
 [exec メソッド \(Regular Expression\)](../../javascript/reference/exec-method-regular-expression-javascript.md)   
 [match メソッド \(String\)](../../javascript/reference/match-method-string-javascript.md)   
 [Regular Expression オブジェクト](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/ja-jp/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [replace メソッド \(String\)](../../javascript/reference/replace-method-string-javascript.md)   
 [test メソッド \(Regular Expression\)](../../javascript/reference/test-method-regular-expression-javascript.md)   
 [Regular Expression Programming \(JavaScript\)](http://msdn.microsoft.com/ja-jp/3b62e27c-4f07-4726-a95b-6e841807bfaf)