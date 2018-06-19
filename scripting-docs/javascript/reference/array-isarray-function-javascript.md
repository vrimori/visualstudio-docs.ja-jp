---
title: Array.isArray 関数 (JavaScript) |Microsoft ドキュメント
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
helpviewer_keywords:
- isArray function [JavaScript]
- Array.isArray function [JavaScript]
ms.assetid: 58f7d2e0-d310-4292-b9bc-37a73c585780
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c31bdfe022cd41648117fc80c8df257e48e592ae
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633472"
---
# <a name="arrayisarray-function-javascript"></a>Array.isArray 関数 (JavaScript)
オブジェクトが配列であるかどうかを判別します。  
  
## <a name="syntax"></a>構文  
  
```  
Array.isArray(object)   
```  
  
#### <a name="parameters"></a>パラメーター  
 `object`  
 必須です。 テストするオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 `object` が配列である場合は `true`。それ以外の場合は `false`。 `object` 引数がオブジェクトではない場合、`false` が返されます。  
  
## <a name="example"></a>例  
 `Array.isArray` 関数の使用例を次に示します。  
  
```JavaScript  
var ar = [];  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = new Array();  
var result = Array.isArray(ar);  
// Output: true  
  
var ar = [1, 2, 3];  
var result = Array.isArray(ar);  
// Output: true  
  
var result = Array.isArray("an array");  
document.write(result);  
// Output: false  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Array オブジェクト](../../javascript/reference/array-object-javascript.md)   
 [配列の使用](../../javascript/advanced/using-arrays-javascript.md)   
 [typeof 演算子](../../javascript/reference/typeof-operator-decrementjavascript.md)