---
title: "substring メソッド (String) (JavaScript) | Microsoft Docs"
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
  - "substring"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "部分文字列"
  - "substring メソッド"
ms.assetid: 9cf9a005-cbe3-42fd-828b-57a39f54224c
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# substring メソッド (String) (JavaScript)
`String` オブジェクトに格納されている文字列内の指定された位置にある部分文字列を返します。  
  
## 構文  
  
```  
  
      strVariable. substring(start [, end])  
"String Literal".substring(start [, end])   
```  
  
## パラメーター  
 `start`  
 必須です。  取得する部分文字列の先頭文字の位置を 0 から始まる値で指定します。  
  
 `end`  
 省略可能です。  必ず指定します。取得する文字列の終了文字の位置を 0 から始まる値で指定します。  部分文字列には、`end` で指定された文字の 1 つ前の文字までが含まれます。  
  
 `end` を省略すると、`start` から元の文字列の末尾の文字までが返されます。  
  
## 解説  
 `substring` メソッドは、`start` から `end` の前の文字までの部分文字列を返します。  
  
 **substring** メソッドでは、引数 `start` と引数 `end` のうち値の小さい方が取得する文字列の先頭位置になります。  たとえば、strvar.substring\(0, 3**\)** と strvar.substring\(3, 0\) は同じ部分文字列を返します。  
  
 引数 `start` または `end` のいずれかが `NaN` または負である場合は、0 に置き換えられます。  
  
 取得した文字列の長さは、`start` と `end` の2 つの引数の差の絶対値になります。  たとえば、strvar.substring\(0, 3\) メソッドと strvar.substring\(3, 0\) で返される部分文字列の長さは 3 になります。  
  
## 使用例  
 **substring** メソッドの使用例を次に示します。  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substring(10, 15);  
document.write(ss);  
  
// Output:  
// brown  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## 参照  
 [substr メソッド \(String\)](../../javascript/reference/substr-method-string-javascript.md)