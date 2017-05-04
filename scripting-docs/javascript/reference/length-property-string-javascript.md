---
title: "length プロパティ (String) (JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "文字列 [Visual Studio]、長さ"
  - "Length プロパティ"
  - "length プロパティ (String)"
ms.assetid: 7dbd4a0e-c24e-4561-9b5b-e75e649a10a4
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# length プロパティ (String) (JavaScript)
`String` オブジェクトの長さを返します。  
  
> [!WARNING]
>  JavaScript の文字列は変更不可であるため、文字列の長さは変更できません。  
  
## 構文  
  
```  
  
      strVariable.length  
"String Literal".length   
```  
  
## 解説  
 `length` プロパティには、`String` オブジェクトの文字数を示す整数が格納されています。  `String` オブジェクトの末尾の文字のインデックス番号は、i`length` \- 1 になります。  
  
## 使用例  
 `length` の使用例を次のコードに示します。  JavaScript の文字列は変更不可で、そのまま変更することはできません。  ただし、逆順にした文字列を配列に書き込み、空の文字で `join` を呼び出して、区切り記号を含まない文字列を生成することができます。  
  
```javascript  
var str = "every good boy does fine";  
        var start = 0;  
        var end = str.length - 1;  
        var tmp = "";  
        var arr = new Array(end);  
  
        while (end >= 0) {  
            arr[start++] = str.charAt(end--);  
        }  
  
// Join the elements of the array with a   
        var str2 = arr.join('');  
        document.write(str2);  
  
// Output: enif seod yob doog yreve  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]