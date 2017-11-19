---
title: "then メソッド (Promise) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: c7f3259d-78f7-4ca7-8bdf-99fbd3f41e8d
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeb97fae19ca9923280b5099e3e4d8c839fa2815
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="then-method-promise"></a>then メソッド (Promise)
Promise が実現したときに実行する作業を指定できるようになります。  
  
## <a name="syntax"></a>構文  
  
```  
  
promise.then(onCompleted, onRejected);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `promise`  
 必須です。 Promise オブジェクト。  
  
 `onCompleted`  
 必須です。 Promise が正常に完了したときに実行する、完了ハンドラー関数。  
  
 `onRejected`  
 省略可能です。 Promise が拒否された場合に実行される、エラー ハンドラー関数。  
  
## <a name="remarks"></a>コメント  
 Promise は、何かの値によって完了するか、または何かの理由によって拒否される必要があります。 Promise オブジェクトの `then` メソッドは、Promise の完了または拒否のどちらか先に生じた方のタイミングで実行されます。 Promise が正常に完了した場合、`then` メソッドの完了ハンドラー関数が実行されます。 Promise が拒否された場合、`then` メソッド (または `catch` メソッド) のエラー ハンドラー関数が実行されます。  
  
## <a name="example"></a>例  
 次の例は、Promise を返す関数 (`timeout`) を呼び出す方法を示しています。 `then` メソッドの完了ハンドラーは、5000 ミリ秒のタイムアウト期限が切れたときに実行されます。  
  
```JavaScript  
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
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Promise オブジェクト](../../javascript/reference/promise-object-javascript.md)