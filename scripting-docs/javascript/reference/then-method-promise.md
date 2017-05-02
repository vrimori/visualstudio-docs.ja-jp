---
title: "then メソッド (Promise) | Microsoft Docs"
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
ms.assetid: c7f3259d-78f7-4ca7-8bdf-99fbd3f41e8d
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# then メソッド (Promise)
Promise が実現したときに実行する作業を指定できるようになります。  
  
## 構文  
  
```  
  
promise.then(onCompleted, onRejected);  
```  
  
#### パラメーター  
 `promise`  
 必須です。  Promise オブジェクト。  
  
 `onCompleted`  
 必須です。  Promise が正常に完了したときに実行する、完了ハンドラー関数。  
  
 `onRejected`  
 省略可能です。  Promise が拒否された場合に実行される、エラー ハンドラー関数。  
  
## 解説  
 Promise は、何かの値によって完了するか、または何かの理由によって拒否される必要があります。  Promise オブジェクトの `then` メソッドは、Promise の完了または拒否のどちらか先に生じた方のタイミングで実行されます。  Promise が正常に完了した場合、`then` メソッドの完了ハンドラー関数が実行されます。  Promise が拒否された場合、`then` メソッド \(または `catch` メソッド\) のエラー ハンドラー関数が実行されます。  
  
## 使用例  
 次の例は、Promise を返す関数 \(`timeout`\) を呼び出す方法を示しています。  `then` メソッドの完了ハンドラーは、5000 ミリ秒のタイムアウト期限が切れたときに実行されます。  
  
```javascript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
// Note: This code uses arrow function syntax  
var m = timeout(5000).then(() => {  
    console.log("done!");  
})  
  
// Output (after 5 seconds):  
// done!  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## 参照  
 [Promise オブジェクト](../../javascript/reference/promise-object-javascript.md)