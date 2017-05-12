---
title: "substr メソッド (String) (JavaScript) | Microsoft Docs"
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
  - "substr"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "substr メソッド"
ms.assetid: f12541c1-2623-482e-941d-2e22bc3c4a4a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# substr メソッド (String) (JavaScript)
文字列内の、指定位置からの指定された長さを持つ部分文字列を取得します。  
  
## 構文  
  
```  
  
stringvar.substr(start [, length ])   
```  
  
## パラメーター  
 `stringvar`  
 必須です。  部分文字列を抽出する文字列リテラルまたは `String` オブジェクトを指定します。  
  
 `start`  
 必須です。  テキストの取り出し開始位置を指定します。  文字列の 1 文字目のインデックス番号は 0 です。  
  
 `length`  
 省略可能です。  取り出す部分の文字数を指定します。  
  
## 解説  
 `length` 引数 に 0 または負の値を指定すると、空の文字列 \(""\) が返されます。  この引数を省略すると、部分文字列が `stringvar` の最後まで取り出されます。  
  
## 使用例  
 `substr` メソッドの使用例を次に示します。  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substr(10, 5);    
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10);  
document.write("[" + ss + "] <br>");  
  
ss = s.substr(10, -5);  
document.write("[" + ss + "] <br>");  
  
// Output:  
// [brown]   
// [brown fox jumps over the lazy dog.]   
// []  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [String オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## 参照  
 [substring メソッド \(String\)](../../javascript/reference/substring-method-string-javascript.md)