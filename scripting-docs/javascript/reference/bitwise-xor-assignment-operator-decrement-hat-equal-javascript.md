---
title: "ビットごとの XOR 代入演算子 (^ =) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: ^=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- ^= operator, about ^= operator
- assignment operators, bitwise [JavaScript]
- bitwise operators, XOR operator
- XOR operator
- ^= operator
ms.assetid: a6ded216-27b6-4fc4-a51b-7d10cc6f820c
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 511ff5b3346bb2b04bf4c24cb3e0b715b2ccf4c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-xor-assignment-operator--javascript"></a>ビットごとの XOR 代入演算子 (^=) (JavaScript)
変数と式に対してビットごとの排他的 OR を実行し、その結果を変数に代入します。  
  
## <a name="syntax"></a>構文  
  
```  
  
result ^= expression  
```  
  
## <a name="parameters"></a>パラメーター  
 *結果*  
 任意の変数。  
  
 *式*  
 任意の式。  
  
## <a name="remarks"></a>コメント  
 使用して、  **^=** 演算子まったく同じであるを指定するとします。  
  
```JavaScript  
result = result ^ expression  
```  
  
 **^=** 演算子の 2 つの式の値をバイナリ形式で、その排他的 OR 演算にします。 この操作の結果は次のように動作します。  
  
```JavaScript  
0101    (result)  
1100    (expression)  
----  
1001    (result)  
```  
  
 のみ 1 つ、式の 1 1 桁の数字で、結果が 1 になります。 それ以外の場合、結果は、そのビットの 0 を持ちます。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ビットごとの XOR 演算子 (^)](../../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)