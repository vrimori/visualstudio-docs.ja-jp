---
title: "Object.getOwnPropertySymbols 関数 (JavaScript) | Microsoft Docs"
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
ms.assetid: 68dd69b9-5a33-44c2-ba5f-21a4ae6c0879
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# Object.getOwnPropertySymbols 関数 (JavaScript)
オブジェクトの独自のシンボル プロパティを返します。  オブジェクトの独自のシンボル プロパティは、オブジェクトのプロトタイプから継承されたものではなく、そのオブジェクトに直接定義されたプロパティです。  
  
## 構文  
  
```  
Object.getOwnPropertySymbols(object);  
```  
  
#### パラメーター  
 `object`  
 必須です。  独自のシンボルを含むオブジェクト。  
  
## 戻り値  
 オブジェクトの独自のシンボルを含む配列。  
  
## 解説  
 オブジェクトのシンボル プロパティを取得するには、`Object.getOwnPropertySymbols` を使用する必要があります。  `Object.getOwnPropertyNames` はシンボル プロパティを返しません。  
  
## 使用例  
 次のコード例では、オブジェクトのシンボル プロパティを取得する方法を示しています。  
  
```javascript  
var obj = {};  
var key = Symbol('description');  
  
obj[key] = 'data';  
  
var symbols = Object.getOwnPropertySymbols(obj);  
  
console.log(s[0].toString());  
  
// Output:  
// undefined  
// Symbol(description)  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]