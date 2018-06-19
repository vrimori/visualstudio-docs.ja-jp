---
title: push メソッド (Array) (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- push
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Push method
ms.assetid: fa6e5799-dabe-4b3d-bd1f-0afc68c77134
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ddb49f310eaff51fe9e9ba584281fdf07bc2e818
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639452"
---
# <a name="push-method-array-javascript"></a>push メソッド (Array) (JavaScript)
配列に新しい要素を追加し、その要素を追加した後の配列の長さを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
arrayObj.push([item1 [item2 [. . . [itemN ]]]])  
```  
  
## <a name="parameters"></a>パラメーター  
 `arrayObj`  
 必須です。 `Array` オブジェクト。  
  
 `item, item2,. . ., itemN`  
 省略可能です。 新しい要素の`Array`です。  
  
## <a name="remarks"></a>コメント  
 `push`と`pop`スタックを最初に、最後のシミュレーションを行うメソッドを使用します。  
  
 `push`メソッドが表示される順序で要素を追加します。 配列引数のいずれかの場合は、単一の要素として追加されます。 使用して、`concat`メソッドを 2 つ以上の配列の要素を連結します。  
  
## <a name="example"></a>例  
 `push` メソッドの使用例を次に示します。  
  
```JavaScript  
var number;  
var my_array = new Array();  
  
my_array.push (5, 6, 7);  
my_array.push (8, 9);  
  
number = my_array.pop();  
while (number != undefined)  
   {  
   document.write (number + " ");  
   number = my_array.pop();  
   }  
  
// Output:  
// 9 8 7 6 5  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [concat メソッド (Array)](../../javascript/reference/concat-method-array-javascript.md)   
 [pop メソッド (Array)](../../javascript/reference/pop-method-array-javascript.md)