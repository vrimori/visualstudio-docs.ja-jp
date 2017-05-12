---
title: "Array.from 関数 (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: 1bf59a99-f860-4c4d-b4c6-d5f1f946a490
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Array.from 関数 (Array) (JavaScript)
配列に似たオブジェクトまたは反復可能なオブジェクトから配列を返します。  
  
## 構文  
  
```  
Array.from (arrayLike [ , mapfn [ , thisArg ] ] );  
```  
  
#### パラメーター  
 `arrayLike`  
 必須です。  配列に似たオブジェクトまたは反復可能なオブジェクトです。  
  
 `mapfn`  
 省略可能です。  `arrayLike` で各要素に対して呼び出すマッピング関数です。  
  
 `thisArg`  
 省略可能です。  マッピング関数で `this` オブジェクトを指定します。  
  
## 解説  
 `arrayLike` パラメーターは、`Set` オブジェクトなどの、インデックス付きの要素および `length` プロパティを持つオブジェクトか反復可能なオブジェクトでなければなりません。  
  
 省略可能なマッピング関数は、配列内の各要素に対して呼び出されます。  
  
## 使用例  
 次の例では、DOM 要素ノードのコレクションから配列を返します。  
  
```javascript  
var elemArr = Array.from(document.querySelectorAll('*'));  
var elem = elemArr[0]; // elem contains a reference to the first DOM element  
  
```  
  
## 使用例  
 次の例では、文字の配列を返します。  
  
```javascript  
var charArr = Array.from("abc");  
// charArr[0] == "a";  
```  
  
## 使用例  
 次の例では、コレクションに含まれるオブジェクトの配列を返します。  
  
```javascript  
var setObj = new Set("a", "b", "c");  
var objArr = Array.from(setObj);  
// objArr[1] == "b";  
  
```  
  
## 使用例  
 次の例は、要素の値を変更するために、矢印構文とマッピング関数を使用する方法を示します。  
  
```javascript  
var arr = Array.from([1, 2, 3], x => x * 10);  
// arr[0] == 10;  
// arr[1] == 20;  
// arr[2] == 30;  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]