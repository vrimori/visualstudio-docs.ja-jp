---
title: "String.fromCodePoint 関数 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 7c4c057b-c67a-4b10-afdd-4f75c7c5988c
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# String.fromCodePoint 関数 (JavaScript)
Unicode UTF\-16 コード ポイントに関連付けられた文字列を返します。  
  
## 構文  
  
```  
String.fromCodePoint(...codePoints);  
```  
  
#### パラメーター  
 `…codePoints`  
 必須。  1 つ以上の UTF\-16 コード ポイント値を指定する rest パラメーター。  
  
## 解説  
 この関数は、`...codePoints` が有効な UFT\-16 コード ポイントではない場合には `RangeError` 例外をスローします。  
  
## 使用例  
 次の例は、`fromCodePoint` 関数の使用法を示しています。  
  
```javascript  
var str1 = String.fromCodePoint(0x20BB7);  
var str2 = String.fromCodePoint(98);  
var str3 = String.fromCodePoint(97, 98, 99);  
  
if(console && console.log) {  
    console.log(str1);  
    console.log(str2);  
    console.log(str3);  
}  
  
// Output:  
// 𠮷  
// b  
// abc  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]