---
title: "propertyIsEnumerable メソッド (Object) (JavaScript) | Microsoft Docs"
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
  - "propertyIsEnumerable"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "propertyIsEnumerable プロパティ"
ms.assetid: d90c7c2e-ea23-4710-a957-9aefbbd1f68b
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# propertyIsEnumerable メソッド (Object) (JavaScript)
指定したオブジェクトが列挙可能かどうかを判定します。  
  
## 構文  
  
```  
  
object. propertyIsEnumerable(proName)  
```  
  
## パラメーター  
 `object`  
 必須です。  オブジェクトのインスタンスを指定します。  
  
 `proName`  
 必須です。  プロパティ名の文字列値を指定します。  
  
## 解説  
 `proName` が `object` に存在し、`For` のループを使用して列挙できる場合、`propertyIsEnumerable` メソッドは `true` を返します。  `propertyIsEnumerable` メソッドは、指定した名前のプロパティが `object` にない場合、または指定したプロパティが列挙可能ではない場合に `false` を返します。  一般に、定義済みのプロパティは列挙可能ではありませんが、ユーザー定義のプロパティは常に列挙可能です。  
  
 `propertyIsEnumerable` メソッドは、プロトタイプ チェインのオブジェクトを考慮しません。  
  
## 使用例  
  
```javascript  
var a = new Array("apple", "banana", "cactus");  
document.write(a.propertyIsEnumerable(1));  
  
// Output: true  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## 参照  
 [prototype プロパティ \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)