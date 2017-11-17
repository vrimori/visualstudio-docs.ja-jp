---
title: "unshift メソッド (Array) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: unshift
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: unshift method
ms.assetid: 8c6a39ed-bab3-4ca4-9350-571a9427ec94
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c3f0d210514d04afa5cf467819a5e843925e1a68
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="unshift-method-array-javascript"></a>unshift メソッド (Array) (JavaScript)
配列の先頭に新しい要素を挿入します。  
  
## <a name="syntax"></a>構文  
  
```  
  
arrayObj.unshift([item1[, item2 [, . . . [, itemN]]]])  
```  
  
## <a name="parameters"></a>パラメーター  
 `arrayObj`  
 必須です。 `Array` オブジェクト。  
  
 `item1, item2,. . ., itemN`  
 省略可能です。 先頭に挿入する要素、`Array`です。  
  
## <a name="remarks"></a>コメント  
 `unshift`メソッドは、引数リストに表示される同じ順序で表示されるよう、配列の先頭に要素を挿入します。  
  
## <a name="example"></a>例  
 `unshift` メソッドの使用例を次に示します。  
  
```JavaScript  
var ar = new Array();  
ar.unshift(10, 11);  
ar.unshift(12, 13, 14);  
document.write(ar.toString());  
  
// Output: 12,13,14,10,11  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [shift メソッド (Array)](../../javascript/reference/shift-method-array-javascript.md)