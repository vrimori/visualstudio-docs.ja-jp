---
title: "has メソッド (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 876df854-2941-4db2-92c6-1b497840b169
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# has メソッド (Map) (JavaScript)
マップに指定された要素がある場合は `true` を戻します。  
  
## 構文  
  
```javascript  
mapObj.has(key)  
```  
  
#### パラメーター  
 `mapObj`  
 必須です。  `Map` オブジェクト。  
  
 `key`  
 必須です。  テストする要素のキー。  
  
## プロパティ値\/戻り値  
 マップに指定された要素がある場合は `true` です。  
  
## 使用例  
 次の例は、`Map` にメンバーを追加し、マップ内のそのメンバーの存在を確認する方法を示します。  
  
```javascript  
var m = new Map();  
m.set(2, "red");  
  
document.write(m.has(2));  
  
// Output:  
// true  
```  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]