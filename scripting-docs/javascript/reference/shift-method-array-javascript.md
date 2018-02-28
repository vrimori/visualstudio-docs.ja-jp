---
title: "shift メソッド (Array) (JavaScript) |Microsoft ドキュメント"
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
- shift
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- shift method
ms.assetid: f33baec5-f67e-4760-b7c1-553727bd0423
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 664c3f764950b329cea8356f5b350ee917f0a60f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="shift-method-array-javascript"></a>shift メソッド (Array) (JavaScript)
配列の先頭の要素を削除し、削除した要素を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
arrayObj.shift( )  
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な`arrayObj`参照は、`Array`オブジェクト。  
  
## <a name="return-value"></a>戻り値  
 配列から削除する要素を返します。  
  
## <a name="remarks"></a>コメント  
 `shift` メソッドの使用例を次に示します。  
  
```JavaScript  
var arr = new Array(10, 11, 12);  
while (arr.length > 0)  
    {  
    var i = arr.shift();  
    document.write (i.toString() + " ");  
    }  
  
// Output:   
// 10 11 12  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [unshift メソッド (Array)](../../javascript/reference/unshift-method-array-javascript.md)