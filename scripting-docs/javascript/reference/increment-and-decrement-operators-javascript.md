---
title: "インクリメント (+ +) 演算子とデクリメント (-) 演算子 (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- --
- ++
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- increment operators, syntax
- ++ operator
- ++ operator, about ++ operator
- decrement operators, syntax
- -- operator
ms.assetid: 49eaf4cf-8818-478d-a429-cdd2ece20811
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 806bd321bb1f81d585a6595b8cf2842571164921
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="increment--and-decrement----operators-javascript"></a>インクリメント演算子 (++)、デクリメント演算子 (--) (JavaScript)
インクリメント演算子インクリメントおよびデクリメント演算子をデクリメントして 1 つの変数の値。  
  
## <a name="syntax"></a>構文  
  
```  
  
      result = ++variable  
result = --variable  
result = variable++  
result = variable--  
```  
  
## <a name="parameters"></a>パラメーター  
 `result`  
 任意の変数。  
  
 `variable`  
 任意の変数。  
  
## <a name="remarks"></a>コメント  
 変数の前に、演算子が表示されたら、式が評価される前に、値が変更されます。 変数の後に、演算子が表示されたら、値は、式が評価された後に変更されます。  つまり、指定された`j = ++k;`の値`j`の元の値は、 `k` ; 1 を加算指定`j = k++;`の値`j`の元の値は、 `k`、これにその値が割り当てられた後にインクリメントされます`j`.  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)