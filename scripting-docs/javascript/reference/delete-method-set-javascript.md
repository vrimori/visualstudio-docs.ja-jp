---
title: "delete メソッド (Set) (JavaScript) | Microsoft Docs"
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
ms.assetid: 052c409e-10c9-49f2-955d-5ad7e31c14f3
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# delete メソッド (Set) (JavaScript)
指定された要素をセットから削除します。  
  
## 構文  
  
```javascript  
setObj.delete(value)  
```  
  
#### パラメーター  
 `setObj`  
 必須です。  `Set` オブジェクト。  
  
 `value`  
 必須です。  削除する要素。  
  
## プロパティ値\/戻り値  
 `true` の場合、要素は既に削除されています。  
  
## 使用例  
 次の例は、メンバーを `Set` に追加して、その 1 つを削除する方法を示します。  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
s.delete("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776,  
```  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]