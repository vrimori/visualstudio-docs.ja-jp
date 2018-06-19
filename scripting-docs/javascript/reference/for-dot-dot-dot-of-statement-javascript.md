---
title: データ型.. ステートメント (JavaScript) の |Microsoft ドキュメント
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
ms.assetid: 7872b0b2-5701-4d72-9b52-ed13991542cc
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2373d319347f927304c32cb47856405a1d69a6b2
ms.sourcegitcommit: b400528a83bea06d208d95c77282631ae4a93091
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2018
ms.locfileid: "34454597"
---
# <a name="forof-statement-javascript"></a>for...of ステートメント (JavaScript)
反復可能なオブジェクトから取得した反復子の値ごとに、1 つまたは複数のステートメントを実行します。  
  
## <a name="syntax"></a>構文  
  
```  
for (variable of object) {  
    statements   
}  
```  
  
## <a name="parameters"></a>パラメーター  
 `variable`  
 必須。 `object` の任意のプロパティ値を代入できる変数。  
  
 `object`  
 必須。 反復可能オブジェクトなど、 `Array`、 `Map`、 `Set`、または実装するオブジェクト、[反復子インターフェイス](../../javascript/advanced/iterators-and-generators-javascript.md)です。  
  
 `statements`  
 任意。 `object` の値ごとに実行する 1 つ以上のステートメント。 複合ステートメントにすることもできます。  
  
## <a name="remarks"></a>コメント  
 ループの各反復処理の最初で、`variable` の値は `object` の次のプロパティ値となります。  
  
## <a name="example"></a>例  
 次の例は、配列での `for...of` ステートメントの使用方法を示しています。  
  
```JavaScript  
let arr = [ "fred", "tom", "bob" ];  
  
for (let i of arr) {  
    console.log(i);  
}  
  
// Output:  
// fred  
// tom  
// bob  
  
```  
  
## <a name="example"></a>例  
 次の例は、`Map` オブジェクトでの `for...of` ステートメントの使用方法を示しています。  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
  
for (var n of m) {  
  console.log(n);  
}  
  
// Output:  
// 1,black  
// 2,red  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [データ型… ステートメントで](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md)   
 [for ステートメント](../../javascript/reference/for-statement-javascript.md)   
 [while ステートメント](../../javascript/reference/while-statement-javascript.md)