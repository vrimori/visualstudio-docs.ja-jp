---
title: "ビットごとの AND 演算子 (&amp;) (JavaScript) |Microsoft ドキュメント"
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
- '&'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- assignment operators, bitwise [JavaScript]
- '& operator, about & operator'
- AND operator
- '& operator'
- bitwise operators, AND operator
- '& operator, bitwise operators'
ms.assetid: a8c17a55-2599-4518-98d7-671699f4d5f3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fa8b3eec0cbd7c172d08b16120fb54f3be3c6a48
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-and-operator-amp-javascript"></a>ビットごとの AND 演算子 (&amp;) (JavaScript)
32 ビットの 2 つの式でビットごとの AND 演算を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
result = expression1 & expression2  
```  
  
## <a name="parameters"></a>パラメーター  
 `result`  
 操作の結果。  
  
 `expression1`  
 任意の式。  
  
 `expression2`  
 任意の式。  
  
## <a name="remarks"></a>コメント  
 `&`は 32 ビットの 2 つの式のビットの各ビットごとの AND 演算します。 1 ビットの両方の場合は、結果は 1 です。 それ以外の場合、結果は 0 です。  
  
|Bit1|Bit2|値の and 演算|  
|----------|----------|-----------------|  
|0|0|0|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
  
 次の例を使用する方法を示して、`&`演算子。  
  
```JavaScript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
var result = expr1 & expr2;  
  
document.write(result);  
// Output: 1  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ビットごとの AND 代入演算子 (& =)](../../javascript/reference/bitwise-and-assignment-operator-decrement-equal-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)