---
title: "delete メソッド (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 7d54ae55-e514-45ba-b403-d1eee46837d2
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# delete メソッド (WeakMap) (JavaScript)
`WeakMap` オブジェクトから指定された要素を削除します。  
  
## 構文  
  
```javascript  
weakmapObj.delete(key)  
```  
  
#### パラメーター  
 `weakmapObj`  
 必須です。  `WeakMap` オブジェクト。  
  
 `key`  
 必須です。  削除する要素のキー。  
  
## プロパティ値\/戻り値  
 `true` の場合、要素は既に削除されています。  
  
## 使用例  
 次の例は、`WeakMap` にメンバーを追加して削除する方法を示します。  
  
```javascript  
function Dog(breed) {  
    this.breed = breed;  
}  
  
var dog = new Dog("yorkie");  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.delete(dog);  
```  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]