---
title: "has メソッド (WeakSet) (JavaScript) | Microsoft Docs"
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
ms.assetid: e24f0876-26bd-4007-b12a-360bb6fa0951
caps.latest.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 2
---
# has メソッド (WeakSet) (JavaScript)
指定された要素が `WeakSet` にある場合は `true` を返します。  
  
## 構文  
  
```javascript  
setObj.has(obj)  
```  
  
#### パラメーター  
 `setObj`  
 必須。  `WeakSet` オブジェクト。  
  
 `obj`  
 必須。  テストする要素。  
  
## プロパティ値\/戻り値  
 セットに指定された要素がある場合は `true` です。  
  
## 使用例  
 次の例は、`WeakSet` にメンバーを追加し、セット内の特定メンバーの存在を確認する方法を示します。  
  
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