---
title: "Promise.all 関数 (Promise) |Microsoft ドキュメント"
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
ms.assetid: 02a7b90c-96f6-4484-9466-d261efa1b494
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 997a419a990b407ae018f7da39fd75673ea28b6d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="promiseall-function-promise"></a>Promise.all 関数 (Promise)
2 つ以上の Promise を結合して、指定されたすべての Promise が完了するか拒否された場合にのみ返ります。  
  
## <a name="syntax"></a>構文  
  
```  
Promise.all(func1, func2 [,funcN])  
```  
  
#### <a name="parameters"></a>パラメーター  
 `func1`  
 必須です。 Promise を返す関数。  
  
 `func2`  
 必須です。 Promise を返す関数。  
  
 `funcN`  
 省略可能です。 Promise を返す 1 つ以上の関数。  
  
## <a name="remarks"></a>コメント  
 返される結果は、完了した Promise によって返される値の配列です。 結合された Promise のいずれかが拒否された場合、`Promise.all` は拒否された Promise の理由と共に直ちに返ります (他のすべての返り値は破棄されます)。  
  
## <a name="example"></a>例  
 このコードでは、タイムアウトへの最初の呼び出しが 5000 ミリ秒後に返ります。 終了ハンドラーは `Promise.all` を呼び出します。これはタイムアウトへの両方の呼び出しが完了したか拒否された場合にのみ返ります。  
  
```JavaScript  
function timeout(duration) {  
    return new Promise(function(resolve, reject) {  
        setTimeout(resolve, duration);  
    });  
}  
  
var p = timeout(5000).then(() => {  
    return Promise.all([timeout(100), timeout(200)]);  
})  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Promise オブジェクト](../../javascript/reference/promise-object-javascript.md)