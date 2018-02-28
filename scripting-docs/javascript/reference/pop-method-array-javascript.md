---
title: "pop メソッド (Array) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- pop
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Pop method
ms.assetid: 4fae7f98-29f1-4041-ba43-601f2e5145ec
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f7635ddcc1b3d336f5e3de66e62714bd93a06158
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="pop-method-array-javascript"></a>pop メソッド (Array) (JavaScript)
配列の最後の要素を削除し、削除した要素を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
arrayObj.pop( )  
```  
  
## <a name="remarks"></a>コメント  
 [プッシュ](../../javascript/reference/push-method-array-javascript.md)と`pop`メソッドを使用すると、シミュレート、スタックは、まず先出し (LIFO) のデータを格納するには、最後の原則を使用します。  
  
 必要な`arrayObj`参照は、`Array`オブジェクト。  
  
 配列が空の場合、`undefined`が返されます。  
  
## <a name="example"></a>例  
 `pop` メソッドの使用例を次に示します。  
  
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
  
// Output: 9 8 7 6 5  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [push メソッド (Array)](../../javascript/reference/push-method-array-javascript.md)