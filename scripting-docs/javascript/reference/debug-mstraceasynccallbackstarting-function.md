---
title: Debug.msTraceAsyncCallbackStarting 関数 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 0e2ca7c4-103c-44f2-b76c-102fb1e42543
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 49203cdf16e7cbd74493c882d9cf17b7629da79a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636252"
---
# <a name="debugmstraceasynccallbackstarting-function"></a>Debug.msTraceAsyncCallbackStarting 関数
以前に指定された非同期操作とコールバックのスタックを関連付けます。  
  
## <a name="syntax"></a>構文  
  
```  
Debug.msTraceAsyncCallbackStarting(asyncOperationId)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `asyncOperationId`  
 必須です。 非同期操作に関連付けられた ID。  
  
## <a name="remarks"></a>コメント  
 `Debug.msTraceAsyncOperationCompleted` を呼び出した後に、非同期操作のコールバック関数で、この関数を呼び出します。  
  
> [!NOTE]
>  デバッグ ツールによっては、デバッガーに送信される情報を表示しません。  
  
 `asyncOperationId` は、`Debug.msTraceAsyncOperationStarting` から以前に返された操作の名前に対応する必要があります。  
  
## <a name="example"></a>例  
 次のコードは [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] アプリケーションの非同期呼び出しのトレースの例を示します。  
  
```JavaScript  
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
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]