---
title: "ビット演算子 OR 代入演算子 (| =) (JavaScript) |Microsoft ドキュメント"
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
- '|='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- assignment operators, bitwise [JavaScript]
- '|= operator'
- bitwise operators, OR operator
- OR operator
ms.assetid: 9b424ff6-4442-4621-b3b6-83e7fd1e5cd5
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ce9cadcf07906c9eba6749706620ae6293c2682
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-or-assignment-operator--javascript"></a>ビットごとの OR 代入演算子 (|=) (JavaScript)
変数の値と式の値に対してビットごとの OR を実行し、その結果を変数に代入します。  
  
## <a name="syntax"></a>構文  
  
```  
  
result |= expression  
```  
  
## <a name="parameters"></a>パラメーター  
 *結果*  
 任意の変数。  
  
 *式*  
 任意の式。  
  
## <a name="remarks"></a>コメント  
 この演算子を使ってまったく同じであるを指定するとします。  
  
```JavaScript  
result = result | expression  
```  
  
 **&#124; =**演算子の値のバイナリ表現を見ます*結果*と*式*にビットごとの OR 演算の場合は。 この操作の結果は、次のように動作します。  
  
```JavaScript  
0101    (result)  
1100    (expression)  
----  
1101    (output)  
```  
  
 どちらか一方の式の 1 1 桁の数字で、結果が 1 になります。 それ以外の場合、結果は、そのビットの 0 を持ちます。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ビットごとの OR 演算子 (&#124;)](../../javascript/reference/bitwise-or-operator-decrement-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)