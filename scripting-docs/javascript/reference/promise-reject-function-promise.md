---
title: "Promise.reject 関数 (Promise) |Microsoft ドキュメント"
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
ms.assetid: 9746e15b-9717-4e36-bf6b-910dcc6cd667
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0711bdd8a478d4ea07ee40ea6822af3c8c4ac610
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="promisereject-function-promise"></a>Promise.reject 関数 (Promise)
渡された引数と等しい結果の、新しい拒否された Promise を作成します。  
  
## <a name="syntax"></a>構文  
  
```  
Promise.reject(r);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `r`  
 必須です。 Promise が拒否された理由。  
  
## <a name="remarks"></a>コメント  
 拒否された Promise が返されると、`then` または `catch` メソッドのエラー処理関数を実行します。  
  
## <a name="example"></a>例  
  
```JavaScript  
var p = Promise.reject('failure');  
p.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Promise オブジェクト](../../javascript/reference/promise-object-javascript.md)