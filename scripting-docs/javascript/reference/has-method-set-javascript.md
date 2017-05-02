---
title: "has メソッド (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: fb80f2e0-fc5e-4508-af14-1c3b3b833636
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# has メソッド (Set) (JavaScript)
セットに指定された要素がある場合は `true` を戻します。  
  
## 構文  
  
```javascript  
setObj.has(value)  
```  
  
#### パラメーター  
 `setObj`  
 必須です。  `Set` オブジェクト。  
  
 `value`  
 必須です。  テストする要素。  
  
## プロパティ値\/戻り値  
 セットに指定された要素がある場合は `true` です。  
  
## 使用例  
 次の例は、`Set` にメンバーを追加し、セット内の特定メンバーの存在を確認する方法を示します。  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
  
document.write(s.has(1776));  
document.write(s.has("1776"));  
  
// Output:  
// true  
// false  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]