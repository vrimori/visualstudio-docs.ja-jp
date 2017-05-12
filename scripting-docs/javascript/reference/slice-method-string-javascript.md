---
title: "slice メソッド (String) (JavaScript) | Microsoft Docs"
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
  - "slice"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "slice メソッド"
  - "文字列 [Visual Studio], 返す (文字を)"
ms.assetid: 80cd77a6-3718-492e-8e96-f909d8721d91
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# slice メソッド (String) (JavaScript)
文字列の一部分を返します。  
  
## 構文  
  
```  
  
stringObj.slice(start, [end])   
```  
  
## Parameters  
 `stringObj`  
 Required.  `String` オブジェクトまたは文字列リテラル。  
  
 `start`  
 Required.  `stringObj` から抽出する部分の先頭位置をインデックス番号で指定します。  
  
 `end`  
 Optional.  `stringObj` から抽出する部分の末尾位置をインデックス番号で指定します。  部分文字列には、`end` で指定された文字の 1 つ前の文字までが含まれます。  この値を省略すると、`stringObj` の最後まで取り出されます。  
  
## 解説  
 `slice` メソッドは、`stringObj` の指定した部分が格納された `String` オブジェクトを返します。  
  
 `slice` メソッドは、`end` 引数で指定した文字の 1 つ前の文字までをコピーします。  
  
 引数 `start` に負の値を指定した場合、*length* \+ `start` として処理されます。*length* は文字列の長さです。  `end` に負の値を指定すると、それは *length* \+ `end` として扱われます。  `end` を省略すると、`stringObj` の最後までがコピーされます。  `end` で指定した抽出終了位置が `start` で指定した抽出開始位置より前に来る場合、文字は新しい文字列にコピーされません。  
  
## 使用例  
 最初の例では、`slice` メソッドはすべての文字列を返します。  2 番目の例では、`slice` メソッドは最後の文字を除くすべての文字列を返します。  
  
```javascript  
var str1 = "all good boys do fine";  
  
var slice1 = str1.slice(0);  
var slice2 = str1.slice(0,-1);  
var slice3 = str1.slice(4);  
var slice4 = str1.slice(4, 8);  
  
document.write(slice1 + "<br/>");  
document.write(slice2 + "<br/>");  
document.write(slice3 + "<br/>");  
document.write(slice4);  
  
// Output:  
// all good boys do fine  
// all good boys do fin  
// good boys do fine  
// good  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Applies To**: [String オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## 参照  
 [slice メソッド \(Array\)](../../javascript/reference/slice-method-array-javascript.md)