---
title: 代入演算子 (=) (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- =
- Assign
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- = operator, about = operator
- = operator, assignment operators
- = operator
- assignment operators, JavaScript
ms.assetid: 1c46a560-ec8d-41c5-a806-30c4843789c4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1b89e444d55f5a0a05cbb444b182dac27627d9b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633782"
---
# <a name="assignment-operator--javascript"></a>左シフト代入演算子 (=) (JavaScript)
値を変数に代入します。  
  
## <a name="syntax"></a>構文  
  
```  
  
result = expression  
```  
  
## <a name="parameters"></a>パラメーター  
 `result`  
 任意の変数。  
  
 `expression`  
 任意の数式。  
  
## <a name="remarks"></a>コメント  
 = 演算子は、それを含む式が値を持つように他の演算子のように動作します。 つまり、代入演算子を次のように連鎖できます:`j = k = l = 0`です。 ここでは`j`、 `k`、および`l`ゼロです。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)