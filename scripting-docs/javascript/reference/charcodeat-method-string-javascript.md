---
title: "charCodeAt メソッド (String) (JavaScript) | Microsoft Docs"
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
  - "charCodeAt"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "charCodeAt メソッド"
ms.assetid: 5b0290a7-ee4d-4738-a909-c02ef64a2f1a
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# charCodeAt メソッド (String) (JavaScript)
指定した位置にある文字の Unicode 値を返します。  
  
## 構文  
  
```  
  
strObj. charCodeAt(index)  
```  
  
## パラメーター  
 `strObj`  
 必須です。  `String` オブジェクトまたはリテラル文字列。  
  
 `index`  
 必須です。  文字の位置を 0 から始まるインデックスで指定します。  インデックスで指定した位置に文字がない場合は、`NaN` を返します。  
  
## 解説  
  
## 使用例  
 `charCodeAt` メソッドの使用例を次に示します。  
  
```javascript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";   
document.write(str.charCodeAt(str.length - 1));  
  
// Output: 90   
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 参照  
 [String.fromCharCode 関数](../../javascript/reference/string-fromcharcode-function-javascript.md)