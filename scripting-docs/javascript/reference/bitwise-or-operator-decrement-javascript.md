---
title: "ビット演算子 OR 演算子 (|)(JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '|'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- bitwise operators, OR operator
- OR operator
- '| operator'
ms.assetid: ffc8f758-3151-478e-bafb-fc78f1c469a0
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a91c616c84b9d38154bf936f61fb856a4ebad0f7
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-or-operator--javascript"></a>ビットごとの OR 演算子 (|) (JavaScript)
2 つの式に対してビットごとの OR を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
  
result = expression1 | expression2  
```  
  
## <a name="parameters"></a>パラメーター  
 *結果*  
 任意の変数。  
  
 *expression1*  
 任意の式。  
  
 *expression2*  
 任意の式。  
  
## <a name="remarks"></a>コメント  
 **&#124;**演算子は 2 つの式の値をバイナリ形式で、それらのビットごとの演算を行います。 この操作の結果は次のように動作します。  
  
```JavaScript  
0101   (expression1)  
1100   (expression2)  
----  
1101   (result)  
```  
  
 どちらか一方の式の 1 桁の数字で、1 を持つ、結果が 1 になります。 それ以外の場合、結果は、そのビットの 0 があります。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ビット演算子 OR 代入演算子 (&#124; =)](../../javascript/reference/bitwise-or-assignment-operator-decrement-equal-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)