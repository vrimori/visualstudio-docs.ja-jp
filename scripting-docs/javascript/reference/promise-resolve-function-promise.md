---
title: Promise.resolve 関数 (Promise) |Microsoft ドキュメント
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
ms.assetid: 0fb6bff9-54ab-41be-97d7-04f7e6fe9cff
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6d815c9c23da48c877f7f1d995df8991429375e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638562"
---
# <a name="promiseresolve-function-promise"></a>Promise.resolve 関数 (Promise)
引数と等しい結果の、新しい解決済みの Promise を作成します。  
  
## <a name="syntax"></a>構文  
  
```  
Promise.resolve(x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `x`  
 必須です。 完了した Promise によって返された値です。  
  
## <a name="remarks"></a>コメント  
 完了した Promise オブジェクトが返されると、`then` メソッドの完了操作関数が実行されます。  
  
## <a name="example"></a>例  
  
```JavaScript  
var p = Promise.resolve('success');  
p.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Promise オブジェクト](../../javascript/reference/promise-object-javascript.md)