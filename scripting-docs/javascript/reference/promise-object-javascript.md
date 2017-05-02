---
title: "Promise オブジェクト (JavaScript) | Microsoft Docs"
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
ms.assetid: 358ad98b-f7fa-448c-9ee0-ef1e2a45e9c6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Promise オブジェクト (JavaScript)
まだ計算されていない値に対して作業が完了するようにスケジューリングするメカニズムを提供します。  これは、非同期 API との対話を管理するための抽象化です。  
  
## 構文  
  
```  
var promise = new Promise(function(resolve, reject) { ... });  
```  
  
#### パラメーター  
 `promise`  
 必須です。  Promise が割り当てられる変数名。  
  
 `resolve`  
 必須です。  Promise が正常に完了したことを示すために実行される関数。  
  
 `reject`  
 省略可能です。  Promise がエラーによって拒否されたことを示すために実行される関数。  
  
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
  
## 使用例  
 次のコードに示すように、`then` メソッドへの呼び出しを連鎖させることもできます。  各完了ハンドラー自体は、チェーンをサポートするために Promise を返す必要があります。  同じ `timeout` 関数を呼び出すこのコードでは、タイムアウトに対する最初の呼び出しが 1000 ミリ秒後に返ります。  最初の完了ハンドラーが `timeout` を再び呼び出し、この Promise は 2000 ミリ秒後に返ります。  その後、完了ハンドラーはエラーをスローします。  エラー ハンドラーは `Promise.all` を呼び出します。これはタイムアウトへの両方の呼び出しが完了したか拒否された場合にのみ返ります。  
  
```javascript  
var p = timeout(1000).then(() => {  
    return timeout(2000);  
}).then(() => {  
    throw new Error("error");  
}).catch(err => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## 必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## 関数  
 `Promise` オブジェクトの関数を次の表に示します。  
  
|関数|説明|  
|--------|--------|  
|[Promise.all 関数](../../javascript/reference/promise-all-function-promise.md)|2 つ以上の Promise を結合して、指定されたすべての Promise が完了するか拒否された場合にのみ返ります。|  
|[Promise.race 関数](../../javascript/reference/promise-race-function-promise.md)|渡されたいくつかの引数の間で最初に解決または拒否される Promise と同じ結果値の、解決または拒否される新しい Promise を作成します。|  
|[Promise.reject 関数](../../javascript/reference/promise-reject-function-promise.md)|渡された引数と等しい結果の、新しい拒否された Promise を作成します。|  
|[Promise.resolve 関数](../../javascript/reference/promise-resolve-function-promise.md)|引数と等しい結果の、新しい解決済みの Promise を作成します。|  
  
## メソッド  
 `Promise` オブジェクトのメソッドについて、次の表で説明します。  
  
|メソッド|説明|  
|----------|--------|  
|[catch メソッド](../../javascript/reference/catch-method-promise.md)|Promise が拒否されたときに実行する作業を指定できるようになります。|  
|[then メソッド](../../javascript/reference/then-method-promise.md)|Promise が実現したときに実行する作業を指定できるようになります。|