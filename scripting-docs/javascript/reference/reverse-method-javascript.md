---
title: "reverse メソッド (JavaScript) | Microsoft Docs"
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
  - "reverse"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "配列 [Visual Studio]、反転 (要素の)"
  - "reverse メソッド"
  - "置換 (要素を)"
ms.assetid: 02ab051b-79b8-4646-b502-381671e78c12
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# reverse メソッド (JavaScript)
`Array` の要素を反転させます。  
  
## 構文  
  
```  
  
arrayObj.reverse()   
```  
  
## Parameters  
 `arrayObj`  
 必須です。  任意の `Array` オブジェクトを指定します。  
  
## 戻り値  
 逆順の配列。  
  
## 解説  
 `arrayObj` 参照は必須で、`Array` オブジェクトを指定します。  
  
 `reverse` メソッドは、`Array` オブジェクト内で要素の位置を反転させます。  このメソッドを実行しても、新しい `Array` オブジェクトは作成されません。  
  
 配列内の要素が連続していない場合、`reverse` メソッドを実行すると新しい要素が作成され、配列内の連続していない要素の間に挿入されます。  作成された要素の値は、`undefined` になります。  
  
## 使用例  
 `reverse` メソッドの使用例を次に示します。  
  
```javascript  
var arr = new Array(0,1,2,3,4);   
var reverseArr = arr.reverse();  
document.write(reverseArr);  
  
// Output:  
// 4,3,2,1,0  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## 参照  
 [concat メソッド \(Array\)](../../javascript/reference/concat-method-array-javascript.md)