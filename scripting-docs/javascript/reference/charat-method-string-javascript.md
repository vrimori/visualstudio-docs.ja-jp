---
title: "charAt メソッド (String) (JavaScript) | Microsoft Docs"
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
  - "charAt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "文字列オブジェクト、返す (文字を)"
  - "charAt メソッド"
  - "文字、返す (一部を)"
ms.assetid: 63173e15-17f6-47c5-8f94-98ef1eb04c1a
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# charAt メソッド (String) (JavaScript)
指定されたインデックス番号の位置にある文字を返します。  
  
## 構文  
  
```  
  
strObj. charAt(index)  
```  
  
## パラメーター  
 `strObj`  
 必須です。  `String` オブジェクトまたはリテラル文字列。  
  
 `index`  
 必須です。  文字の位置を 0 から始まるインデックスで指定します。  
  
## 解説  
 `charAt` メソッドの戻り値は、指定された `index` にある文字です。  文字列内の 1 文字目のインデックス番号は 0、2 文字目のインデックス番号は 1 となります。  有効範囲外の `index` の値を指定した場合は空の文字列を返します。  
  
## 使用例  
 `charAt` メソッドの使用例を次に示します。  
  
```javascript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
document.write(str.charAt(str.length - 1));  
  
// Output: Z  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **対象**: [String オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## 参照  
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)