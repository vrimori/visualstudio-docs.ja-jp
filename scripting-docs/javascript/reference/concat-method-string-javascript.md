---
title: "concat メソッド (String) (JavaScript) | Microsoft Docs"
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
  - "concat"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "concat メソッド (String)"
  - "Concat メソッド"
ms.assetid: 5d28ebb2-d534-4179-9297-a4c821ee9f24
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# concat メソッド (String) (JavaScript)
指定された複数の文字列を連結した文字列を返します。  
  
## 構文  
  
```  
  
string1. concat([string2[, string3[, . . . [, stringN]]]])  
```  
  
## パラメーター  
 `string1`  
 必須です。  指定した他の文字列がすべて連結される `String` オブジェクトまたはリテラル文字列を指定します。  
  
 `string2,. . ., stringN`  
 省略可能です。  `string1` の末尾に追加する文字列。  
  
## 解説  
 `concat` メソッドの結果は次のように記述した場合と同じです。`result` \= `string1` \+ `string2` \+ `string3` \+ `stringN`。  元の文字列と結果の文字列のどちらか一方が変更された場合でも、その変更はもう一方の文字列には反映されません。  引数が文字列でない場合は、文字列に変換された後 `string1` に連結されます。  
  
## 使用例  
 `concat` メソッドを文字列に対して使用した例を次に示します。  
  
```javascript  
var str1 = "ABCD"  
var str2 = "EFGH";  
var str3 = "1234";  
var str4 = "5678";  
document.write(str1.concat(str2, str3, str4));  
  
// Output: "ABCDEFGH12345678"  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **対象**: [String オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## 参照  
 [加算演算子 \(\+\)](../../javascript/reference/addition-operator-decrement-javascript.md)