---
title: "splice メソッド (Array) (JavaScript) |Microsoft ドキュメント"
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
- splice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- splice method
ms.assetid: 85fdfb13-e3d9-4c89-b524-3ccee7001c93
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0d56a22244f76f5ce7221c276629907811733d51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="splice-method-array-javascript"></a>splice メソッド (Array) (JavaScript)
配列から要素を削除し、必要に応じて新しい要素を削除位置に挿入し、削除した要素を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
arrayObj.splice(start, deleteCount, [item1[, item2[, . . . [,itemN]]]])  
```  
  
## <a name="parameters"></a>パラメーター  
 `arrayObj`  
 必須です。 `Array` オブジェクト。  
  
 `start`  
 必須です。 要素の削除を開始する配列内の 0 から始まる位置。  
  
 `deleteCount`  
 必須です。 削除する要素の数を指定します。  
  
 `item1, item2,. . ., itemN`  
 省略可能です。 削除した要素の代わりに、配列に挿入する要素。  
  
## <a name="remarks"></a>コメント  
 `splice`メソッドが変更`arrayObj`位置から指定数の要素を削除することによって`start`と新しい要素を挿入します。 削除された要素は、新しいとして返されます`Array`オブジェクト。  
  
## <a name="example"></a>例  
 `splice` メソッドの使用例を次のコードに示します。  
  
```JavaScript  
var arr = new Array("4", "11", "2", "10", "3", "1");  
arr.splice(2, 2, "21", "31");  
document.write(arr);  
  
// Output: 4,11,21,31,3,1  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [slice メソッド (Array)](../../javascript/reference/slice-method-array-javascript.md)