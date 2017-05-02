---
title: "Promise.resolve 関数 (Promise) | Microsoft Docs"
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
ms.assetid: 0fb6bff9-54ab-41be-97d7-04f7e6fe9cff
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Promise.resolve 関数 (Promise)
引数と等しい結果の、新しい解決済みの Promise を作成します。  
  
## 構文  
  
```  
Promise.resolve(x)  
```  
  
#### パラメーター  
 `x`  
 必須です。  完了した Promise によって返された値です。  
  
## 解説  
 完了した Promise オブジェクトが返されると、`then` メソッドの完了操作関数が実行されます。  
  
## 使用例  
  
```javascript  
var p = Promise.resolve('success');  
p.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## 参照  
 [Promise オブジェクト](../../javascript/reference/promise-object-javascript.md)