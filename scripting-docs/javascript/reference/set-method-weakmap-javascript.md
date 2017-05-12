---
title: "set メソッド (WeakMap) (JavaScript) | Microsoft Docs"
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
ms.assetid: 29fc72b1-224f-4f19-8c06-5d926d695b03
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# set メソッド (WeakMap) (JavaScript)
`WeakMap` オブジェクトに新しい要素を追加します。  
  
## 構文  
  
```javascript  
weakmapObj.set(key, value)  
```  
  
#### パラメーター  
 `weakmapObj`  
 必須です。  `WeakMap` オブジェクト。  
  
 `key`  
 必須です。  追加する要素のキーを表すオブジェクト。  これは、オブジェクト参照である必要があります。  
  
 `value`  
 必須です。  追加する要素の値。  
  
## プロパティ値\/戻り値  
 新しいキーと値のペアのある `WeakMap` オブジェクトを戻します。  
  
## 解説  
 既存のキーを使用してコレクションに値を追加する場合、新しい値は元の値を置き換えます。  
  
## 使用例  
 次の例は、`WeakMap` オブジェクトにメンバーを追加する方法を示します。  
  
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
```  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]