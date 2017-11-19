---
title: "Object.assign 関数 (Object) (JavaScript) |Microsoft ドキュメント"
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
ms.assetid: 2dd6b312-dcd3-414e-8d53-088c6341c46d
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c156369299e58eac556d43a87476de2ce09173e1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="objectassign-function-object-javascript"></a>Object.assign 関数 (Object) (JavaScript)
1 つ以上のソース オブジェクトからターゲット オブジェクトに値をコピーします。  
  
## <a name="syntax"></a>構文  
  
```  
Object.assign(target, ...sources );  
```  
  
#### <a name="parameters"></a>パラメーター  
 `target`  
 必須です。 列挙可能なプロパティのコピー先となるオブジェクト。  
  
 `...sources`  
 必須です。 列挙可能なプロパティのコピー元となる 1 つ以上のオブジェクト。  
  
## <a name="exceptions"></a>例外  
 割り当てエラーがある場合、この関数は `TypeError` をスローして、コピー操作が終了します。 ターゲット プロパティが書き込み不可の場合、`TypeError` がスローされます。  
  
## <a name="remarks"></a>コメント  
 この関数はターゲット オブジェクトを返します。 のみ*列挙可能な独自*プロパティは、ソース オブジェクトからターゲット オブジェクトにコピーされます。 この関数を使用して、オブジェクトをマージしたりそのクローンを作成したりすることができます。  
  
 `null` や `undefined` ソースは、空のオブジェクトのように扱われ、ターゲット オブジェクトに影響を与えません。  
  
## <a name="example"></a>例  
 次のコード例では、`Object.assign` を使用してオブジェクトを結合する方法を示します。  
  
```JavaScript  
var first = { name: "Bob" };  
var last = { lastName: "Smith" };  
  
var person = Object.assign(first, last);  
console.log(person);  
  
// Output:  
// { name: "Bob", lastName: "Smith" }   
```  
  
## <a name="example"></a>例  
 次の例では、`Object.assign` を使用してオブジェクトのクローンを作成する方法を示します。  
  
```JavaScript  
var obj = { person: "Bob Smith"};  
var clone = Object.assign({}, obj);  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]