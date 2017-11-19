---
title: "Promise.race 関数 (Promise) |Microsoft ドキュメント"
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
ms.assetid: 9236eced-d313-4d03-8c3e-d89d762b3084
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fedd512f4565009c8429b43b0d9d93de943d13fb
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="promiserace-function-promise"></a>Promise.race 関数 (Promise)
渡されたいくつかの引数の間で最初に解決または拒否される Promise と同じ結果値の、解決または拒否される新しい Promise を作成します。  
  
## <a name="syntax"></a>構文  
  
```  
Promise.race(iterable)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `iterable`  
 必須です。 1 つまたは複数の Promise。  
  
## <a name="remarks"></a>コメント  
 `iterable` 内のいずれかの Promise がすでに解決または拒否された状態になっている場合、`Promise.race` は、その Promise の解決 (または拒否) に使用された値と等しい結果値の、解決または拒否された Promise を同じ方法で返します。 `iterable` 内の複数の Promise がすでに解決または拒否されている場合、`Promise.race` は、反復処理された最初の Promise と同じ方法で解決された約束を返します。 反復可能オブジェクト内の Promise が解決および拒否しない場合、`Promise.race` から返される Promise も解決および拒否しません。  
  
## <a name="example"></a>例  
  
```JavaScript  
var p1 = new Promise(function(resolve, reject) {  
    setTimeout(resolve, 0, 'success');  
});  
var p2 = new Promise(function(resolve, reject) { });  
var p2 = new Promise(function(resolve, reject) { });  
  
var race = Promise.race( [p1, p2, p3] );  
race.then(function(result) {  
    console.log(result);  
});  
  
// Output:  
// success  
  
var race = Promise.race( [Promise.reject('failure'),  
    Promise.resolve('success')] );  
race.catch(function(result) {  
    console.log(result);  
});  
  
// Output:  
// failure  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Promise オブジェクト](../../javascript/reference/promise-object-javascript.md)