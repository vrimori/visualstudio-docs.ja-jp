---
title: "has メソッド (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 12bedca1-bde7-413a-a4e2-06c03559044f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# has メソッド (WeakMap) (JavaScript)
`WeakMap` オブジェクトに指定された要素がある場合は `true` を戻します。  
  
## 構文  
  
```javascript  
weakmapObj.has(key)  
```  
  
#### パラメーター  
 `weakmapObj`  
 必須です。  `WeakMap` オブジェクト。  
  
 `key`  
 必須です。  テストする要素のキー。  
  
## プロパティ値\/戻り値  
 `WeakMap` に指定したキーがある場合は、`true`。  
  
## 使用例  
 次の例は、`WeakMap` にメンバーを追加し、`has` を使用してそのメンバーの存在を確認する方法を示します。  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
  
document.write(wm.has(dog));  
  
// Output:  
// true  
```  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]