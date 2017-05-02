---
title: "Debug.msTraceAsyncOperationCompleted 関数 | Microsoft Docs"
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
ms.assetid: 9b628b71-61f1-478a-857f-5e1f607db56c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Debug.msTraceAsyncOperationCompleted 関数
非同期操作が完了したことを示します。  
  
## 構文  
  
```  
Debug.msTraceAsyncOperationCompleted(asyncOperationId, status)  
```  
  
#### パラメーター  
 `asyncOperationId`  
 必ず指定します。  非同期操作に関連付けられた ID。  
  
 `status`  
 省略可能です。  非同期操作の状態。  指定しない場合は、`Debug.MS_ASYNC_OP_STATUS_SUCCESS` が使用されます。  
  
## 解説  
 非同期操作の完了時にこの関数を呼び出します。  
  
 `asyncOperationId` は、`Debug.msTraceAsyncOperationStarting` から以前に返された操作の ID に対応する必要があります。  
  
 `status` は次のような値となります。  
  
-   `Debug.MS_ASYNC_OP_STATUS_SUCCESS`  
  
-   `Debug.MS_ASYNC_OP_STATUS_CANCELED`  
  
-   `Debug.MS_ASYNC_OP_STATUS_ERROR`  
  
> [!NOTE]
>  デバッグ ツールによっては、デバッガーに送信される情報を表示しません。  
  
## 使用例  
 次のコードは [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリケーションの非同期呼び出しのトレースの例を示します。  
  
```javascript  
function asyncWrapperFunction() {  
    var opID = Debug.msTraceAsyncOperationStarting('async trace');  
    doSomethingAsync().then(function (result) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_SUCCESS);  
        Debug.msTraceAsyncCallbackStarting(opID);  
        // Process result of async operation.  
    }, function (error) {  
        Debug.msTraceAsyncOperationCompleted(opID, Debug.MS_ASYNC_OP_STATUS_ERROR);  
        Debug.msTraceAsyncCallbackStarting(opID);  
    });  
  
    Debug.msTraceAsyncCallbackCompleted();  
}  
  
function doSomethingAsync() {  
    return WinJS.Promise.as(true);  
}  
  
asyncWrapperFunction();  
```  
  
## 必要条件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]