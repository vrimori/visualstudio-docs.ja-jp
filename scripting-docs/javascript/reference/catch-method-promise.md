---
title: catch メソッド (Promise) |Microsoft ドキュメント
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
ms.assetid: 55266f6a-db4d-4de8-857a-8bc7d35ed4b8
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 307e5b2a501b038542a602df4538523a3fc6eccd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633992"
---
# <a name="catch-method-promise"></a>catch メソッド (Promise)
Promise が拒否されたときに実行する作業を指定できるようになります。  
  
## <a name="syntax"></a>構文  
  
```  
  
promise.catch(onRejected)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `promise`  
 必須です。 Promise オブジェクト。  
  
 `onRejected`  
 必須です。 Promise が拒否された場合に実行される、エラー ハンドラー関数。  
  
## <a name="remarks"></a>コメント  
  
## <a name="example"></a>例  
 次のコード例では、タイムアウトへの最初の呼び出しが 5000 ミリ秒後に返ります。 このコードで、Promise が拒否されたので、エラー ハンドラー関数が実行されます。  
  
```JavaScript  
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
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]