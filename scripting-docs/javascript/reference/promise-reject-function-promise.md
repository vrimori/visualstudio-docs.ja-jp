---
title: "Promise.reject 関数 (Promise) | Microsoft Docs"
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
ms.assetid: 9746e15b-9717-4e36-bf6b-910dcc6cd667
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Promise.reject 関数 (Promise)
渡された引数と等しい結果の、新しい拒否された Promise を作成します。  
  
## 構文  
  
```  
Promise.reject(r);  
```  
  
#### パラメーター  
 `r`  
 必須です。  Promise が拒否された理由。  
  
## 解説  
 拒否された Promise が返されると、`then` または `catch` メソッドのエラー処理関数を実行します。  
  
## 使用例  
  
```javascript  
var p = Promise.reject('failure');  
p.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## 参照  
 [Promise オブジェクト](../../javascript/reference/promise-object-javascript.md)