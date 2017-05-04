---
title: "set メソッド (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: 31ee71a0-b09d-442a-9e02-825accf94ffa
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# set メソッド (Map) (JavaScript)
マップに新しい要素を追加します。  
  
## 構文  
  
```javascript  
mapObj.set(key, value)  
```  
  
#### パラメーター  
 `mapObj`  
 必須です。  `Map` オブジェクト。  
  
 `key`  
 必須です。  新しい要素のキー。  
  
 `value`  
 必須です。  追加する要素の値。  
  
## プロパティ値\/戻り値  
 新しいキーと値のペアのある `Map` オブジェクトを戻します。  
  
## 解説  
 既存のキーを使用してコレクションに値を追加する場合、新しい値は元の値を置き換えます。  
  
## 使用例  
 次の例は、メンバーを `Map` に追加して取得する方法を示します。  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// black  
// red  
// 2  
```  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]