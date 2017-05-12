---
title: "catch メソッド (Promise) | Microsoft Docs"
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
ms.assetid: 55266f6a-db4d-4de8-857a-8bc7d35ed4b8
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# catch メソッド (Promise)
Promise が拒否されたときに実行する作業を指定できるようになります。  
  
## 構文  
  
```  
  
promise.catch(onRejected)  
```  
  
#### パラメーター  
 `promise`  
 必須です。  Promise オブジェクト  
  
 `onRejected`  
 必須です。  Promise が拒否された場合に実行される、エラー ハンドラー関数。  
  
## 解説  
  
## 使用例  
 次のコード例では、タイムアウトへの最初の呼び出しが 5000 ミリ秒後に返ります。  このコードで、Promise が拒否されたので、エラー ハンドラー関数が実行されます。  
  
```javascript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(reject, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    console.log("done!");  
}).catch(err => {  
    console.log("error!");  
})  
  
// Output (after five seconds):  
// error!  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]