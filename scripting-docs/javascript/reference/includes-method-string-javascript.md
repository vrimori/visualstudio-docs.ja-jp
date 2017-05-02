---
title: "includes メソッド (String) (JavaScript) | Microsoft Docs"
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
ms.assetid: 2639e4e5-23ba-424a-80ea-be067a4cd65e
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# includes メソッド (String) (JavaScript)
渡された文字列が文字列オブジェクトに含まれているかどうかを示すブール値を返します。  
  
## 構文  
  
```  
stringObj.includes(substring [, position]);  
```  
  
#### パラメーター  
 `stringObj`  
 必須です。  テスト対象の文字列オブジェクトです。  
  
 `substring`  
 必須です。  テストする文字列。  
  
 `position`  
 省略可能です。  文字列オブジェクトに存在するかテストする、最初の文字の位置です \(0 から始まります\)。  
  
## 戻り値  
 渡された文字列が文字列オブジェクトに含まれる場合、`includes` メソッドは `true` を返します。それ以外の場合は、`false` を返します。  
  
## 解説  
  
## 使用例  
  
```javascript  
// Returns true   
"abcde".includes("cd")  
"abcde".includes("cd", 2)  
  
// Returns false  
"abcde".includes("CD")  
"abcde".includes("cd", 3)  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]