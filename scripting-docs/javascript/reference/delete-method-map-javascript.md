---
title: "delete メソッド (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: a073e1a1-5862-485b-b2bd-26c66a3aff51
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# delete メソッド (Map) (JavaScript)
指定された要素をマップから削除します。  
  
## 構文  
  
```javascript  
mapObj.delete(key)  
```  
  
#### パラメーター  
 `mapObj`  
 必須です。  `Map` オブジェクト。  
  
 `key`  
 必須です。  削除する要素のキー。  
  
## プロパティ値\/戻り値  
 `true` の場合、要素は既に削除されています。  
  
## 使用例  
 次の例は、メンバーを `Map` に追加して、その 1 つを削除する方法を示します。  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.delete(1);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// red  
// 2  
```  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]