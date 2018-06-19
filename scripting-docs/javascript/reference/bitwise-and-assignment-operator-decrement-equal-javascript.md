---
title: ビットごとの AND 代入演算子 (&amp;=) (JavaScript) |Microsoft ドキュメント
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
- '&='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '&= operator'
- assignment operators, bitwise [JavaScript]
- AND operator
- bitwise operators, AND operator
ms.assetid: e7e2eabb-4fc1-4fdc-9dd8-1e6d715371fa
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dfd2a77e66296cafc6c8403570f0536e1333e081
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634042"
---
# <a name="bitwise-and-assignment-operator-amp-javascript"></a>ビットごとの AND 代入演算子 (&amp;=) (JavaScript)
変数の値のビットごとの AND 演算の結果と式の値を設定します。 変数と式は、32 ビット整数値として扱われます。  
  
## <a name="syntax"></a>構文  
  
```  
  
result &= expression  
```  
  
## <a name="parameters"></a>パラメーター  
 `result`  
 任意の変数。  
  
 `expression`  
 任意の式。  
  
## <a name="remarks"></a>コメント  
 この演算子を使用する方法を指定することと同じです。  
  
```JavaScript  
result = result & expression  
```  
  
 [ビットごとの AND 演算子 (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)の値をバイナリ形式で`result`と`expression`にビットごとの AND 演算の場合は。 この操作の出力は、次のように動作します。  
  
```JavaScript  
// 9 is 00000000000000000000000000001001  
var expr1 = 9;  
  
// 5 is 00000000000000000000000000000101  
var expr2 = 5;  
  
// 1 is 00000000000000000000000000000001  
expr1 &= expr2;  
  
document.write(expr1);  
```  
  
 いつでも、数字で 1 がある式の両方の結果は、そのビットの値 1 を持ちます。 それ以外の場合、結果は、そのビットの 0 を持ちます。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ビットごとの AND 演算子 (&)](../../javascript/reference/bitwise-and-operator-decrement-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)