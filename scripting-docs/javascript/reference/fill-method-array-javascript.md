---
title: "fill メソッド (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: 11526627-c0bb-4157-a8c4-0a039079b4a1
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# fill メソッド (Array) (JavaScript)
指定された値を配列に設定します。  
  
## 構文  
  
```  
arrayObj.fill(value [ , start [ , end ] ]);  
```  
  
#### パラメーター  
 `arrayObj`  
 必須です。  Array オブジェクトです。  
  
 `value`  
 必須です。  配列の設定に使用する値です。  
  
 `start`  
 省略可能です。  配列値の設定に使用する開始インデックスです。  既定値は 0 です。  
  
 `end`  
 省略可能です。  配列値の設定に使用する終了インデックスです。  既定値は、`this` オブジェクトの length プロパティです。  
  
## 解説  
 `start` が負の場合、`start` は `length`\+`start` として扱われます。ここで、`length` は配列の長さです。  `end` が負の場合、`end` は `length`\+`end` として扱われます。  
  
## 使用例  
 次のコードの例は、値を配列に設定します。  
  
```javascript  
[0, 0, 0].fill(7, 1);  
// Array contains [0,7,7]  
  
[0, 0, 0].fill(7);  
// Array contains [7,7,7]  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]