---
title: "Debug.msTraceAsyncOperationStarting 関数 | Microsoft Docs"
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
ms.assetid: c8458264-07e0-4cd6-8528-ff7cf009cf9e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Debug.msTraceAsyncOperationStarting 関数
非同期操作のトレースを開始します。  
  
## 構文  
  
```  
Debug.msTraceAsyncOperationStarting(operationName)  
```  
  
#### パラメーター  
 `operationName`  
 必ず指定します。  非同期操作を識別する文字列。  `operationName` が null または未定義の場合、操作名として空の文字列が使用されます。  
  
## 戻り値  
 操作 ID を表す整数。  
  
## 解説  
 非同期操作の開始前に、このメソッドを呼び出します。  
  
> [!NOTE]
>  デバッグ ツールによっては、デバッガーに送信される情報を表示しません。  
  
## 使用例  
 次のコードは [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリケーションの非同期呼び出しのインストルメントの例を示します。  
  
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