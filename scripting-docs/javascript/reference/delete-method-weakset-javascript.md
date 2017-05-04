---
title: "delete メソッド (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: 19e93366-7d42-4abf-b7b9-fcf943fa17a3
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# delete メソッド (WeakSet) (JavaScript)
指定された要素を `WeakSet` から削除します。  
  
## 構文  
  
```javascript  
weaksetObj.delete(obj)  
```  
  
#### パラメーター  
 `weaksetObj`  
 必須。  `WeakSet` オブジェクト。  
  
 `obj`  
 必須。  削除する要素。  
  
## プロパティ値\/戻り値  
 `true` の場合、要素は既に削除されています。  
  
## 使用例  
 次の例は、`WeakSet` の要素を追加および削除する方法を示しています。  
  
```javascript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]