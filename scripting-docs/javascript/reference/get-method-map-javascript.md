---
title: "get メソッド (Map) (JavaScript) | Microsoft Docs"
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
ms.assetid: bebbd6bc-6e61-4674-8196-7e907798973f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# get メソッド (Map) (JavaScript)
指定された要素をマップから戻します。  
  
## 構文  
  
```javascript  
mapObj.get(key)  
```  
  
#### パラメーター  
 `mapObj`  
 必須です。  `Map` オブジェクト。  
  
 `key`  
 必須です。  `Map` 中の要素のキーです。  
  
## プロパティ値\/戻り値  
 キーに関連付けられているオブジェクトを戻します。  `Map` にキーがない場合、このメソッドは `undefined` 値を戻します。  
  
## 使用例  
 次の例は、`Map` オブジェクトから指定した要素を取得する方法を示します。  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
document.write(m.get(2));  
  
// Output:  
// red  
  
```  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]