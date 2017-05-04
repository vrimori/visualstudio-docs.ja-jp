---
title: "get メソッド (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: d922c55d-486d-4feb-aedc-1f4867c417d2
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# get メソッド (WeakMap) (JavaScript)
指定した要素を `WeakMap` オブジェクトから戻します。  
  
## 構文  
  
```javascript  
weakmapObj.get(key)  
```  
  
#### パラメーター  
 `weakmapObj`  
 必須です。  `WeakMap` オブジェクト。  
  
 `key`  
 必須です。  `WeakMap` 中の要素のキーです。  
  
## プロパティ値\/戻り値  
 キーに関連付けられているオブジェクトを戻します。  `WeakMap` にキーがない場合、このメソッドは `undefined` 値を戻します。  
  
## 使用例  
 次の例は、`WeakMap` オブジェクトからメンバーを取得する方法を示します。  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]