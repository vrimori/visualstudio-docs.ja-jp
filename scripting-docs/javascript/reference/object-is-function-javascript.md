---
title: "Object.is 関数 (JavaScript) | Microsoft Docs"
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
ms.assetid: 6e2f6c6d-7cd2-47c4-a513-3ba53988d27d
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Object.is 関数 (JavaScript)
2 つの値が同じ値であるかどうかを示す値を返します。  
  
## 構文  
  
```javascript  
Object.is(value1, value2)  
```  
  
#### パラメーター  
 `value1`  
 必須です。  テストする 1 番目の値。  
  
 `value2`  
 必須です。  テストする 2 番目の値。  
  
## 戻り値  
 値が同じ値の場合には `true`、それ以外の場合は `false`。  
  
## 解説  
 `Object.is` は \=\= 演算子と異なり、値をテストするときに型を強制しません。  
  
 `Object.is` によって適用される比較は、`Object.is` が `Number.isNaN` を `NaN` と同じ値として扱うことを除いて、\=\=\= 演算子によって適用される比較に似ています。  また、これは \+0 と \-0 を異なる値として扱います。  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]