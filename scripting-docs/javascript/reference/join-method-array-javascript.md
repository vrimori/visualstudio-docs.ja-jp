---
title: "join メソッド (Array) (JavaScript) | Microsoft Docs"
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
  - "join"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Join メソッド"
  - "連結 (文字列を)、join メソッド"
  - "配列 [Visual Studio]、結合"
ms.assetid: 20f8fde1-014b-488e-9008-464a86e6b21f
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# join メソッド (Array) (JavaScript)
指定した区切り記号文字列で区切られた配列内のすべての要素を追加します。  
  
## 構文  
  
```  
  
arrayObj.join([separator])   
```  
  
## パラメーター  
 `arrayObj`  
 必須です。  `Array` オブジェクト。  
  
 `separator`  
 省略可能です。  結果の `String` で配列要素の区切り文字として使用する文字列を指定します。  省略した場合、各配列要素はコンマで区切られます。  
  
## 解説  
 **undefined** または `null` の要素は、空の文字列として処理されます。  
  
## 使用例  
 **join** メソッドの使用例を次に示します。  
  
```javascript  
var a, b;  
a = new Array(0,1,2,3,4);  
b = a.join("-");  
document.write(b);  
  
// Output:  
// 0-1-2-3-4  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 参照  
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)