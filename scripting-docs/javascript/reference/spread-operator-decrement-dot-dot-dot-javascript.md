---
title: "Spread 演算子 (...)(JavaScript) |Microsoft ドキュメント"
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
ms.assetid: 10263a4c-bd27-4d87-9917-fb4b6bf373db
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a07d480360441906c445faa196f6d7771f97d75d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="spread-operator--javascript"></a>Spread 演算子 (...) (JavaScript)
配列リテラルの一部を (別の配列リテラルなどの) 反復可能な式から初期化したり、式を (関数呼び出しで) 複数の引数に拡張したりできます。  
  
## <a name="syntax"></a>構文  
  
```  
var array = [[arg0ToN ,] ...iterable [, arg0ToN]]  
func([args ,] ...iterable [, args | ...iterable])  
  
```  
  
## <a name="parameters"></a>パラメーター  
 `iterable`  
 必須です。 反復可能オブジェクト。  
  
 `arg0ToN`  
 省略可能です。 配列リテラルの 1 つ以上の要素。  
  
 `args`  
 省略可能です。 関数への 1 つ以上の引数。  
  
## <a name="remarks"></a>コメント  
 反復子の詳細については、次を参照してください。[反復子とジェネレーター](../../javascript/advanced/iterators-and-generators-javascript.md)です。 Rest パラメーターとして spread 演算子を使用する方法については、次を参照してください。[関数](../../javascript/functions-javascript.md)です。  
  
## <a name="example"></a>例  
 次のコード例では、spread 演算子と `concat` メソッドの使用法が対比されています。  
  
```JavaScript  
var a, b, c, d, e;  
a = [1,2,3];  
b = "dog";  
c = [42, "cat"];  
  
// Using the concat method.  
d = a.concat(b, c);  
  
// Using the spread operator.  
e = [...a, b, ...c];  
  
console.log(d);  
console.log(e);  
  
// Output:  
// 1, 2, 3, "dog", 42, "cat"  
// 1, 2, 3, "dog", 42, "cat"  
```  
  
## <a name="example"></a>例  
 次のコード例は、関数呼び出しで spread 演算子を使用する方法について示しています。 この例では 2 つの配列リテラルが、spread 演算子を使用する関数に渡され、配列が複数の引数に拡張されます。  
  
```JavaScript  
function f(a, b, c, x, y, z) {  
  return a + b + c + x + y + z;  
}  
  
var args = [1, 2, 3];  
console.log(f(...args, 4, ...[5, 6]));  
  
// Output:  
// 21  
  
```  
  
## <a name="example"></a>例  
 spread 演算子を使用すると、これまでは `apply` を使用する必要があったコードを簡略化できます。  
  
```JavaScript  
function f(x, y, z) {  
    return x + y + z;  
}  
  
var args = [1, 2, 3];  
  
// Old method  
f.apply(this, args);  
// New method  
f(...args);  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)