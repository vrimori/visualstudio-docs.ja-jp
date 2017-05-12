---
title: "add メソッド (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: d35d0287-6b33-4720-b9d7-8954c428ce4e
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# add メソッド (WeakSet) (JavaScript)
`WeakSet` オブジェクトに新しい要素を追加します。  
  
## 構文  
  
```javascript  
weaksetObj.add(obj)  
```  
  
#### パラメーター  
 `weaksetObj`  
 必須。  `WeakSet` オブジェクト。  
  
 `obj`  
 必須。  `WeakSet` の新しい要素を指定します。  
  
## 解説  
 新しい要素は、任意の値ではなくオブジェクトで、なおかつ一意でなければなりません。  `WeakSet` に一意でない要素を追加する場合、新しい要素はコレクションに追加されません。  
  
## 使用例  
 次の例は、メンバーをセットに追加し、その後、メンバーが追加されたことを確認する方法を示しています。  
  
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