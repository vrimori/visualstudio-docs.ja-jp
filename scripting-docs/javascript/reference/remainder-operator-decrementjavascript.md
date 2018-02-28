---
title: "Remainder 演算子 (JavaScript) |Microsoft ドキュメント"
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
- '%'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- remainder operator, JavaScript
- '% operator [JavaScript]'
- Remainder function [JavaScript]
ms.assetid: 087d654f-623b-498d-95ff-596d26bf674d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce74b8512b25cfe215d294873102b274623b42a2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="remainder-operator-javascript"></a>剰余演算子 (JavaScript)
1 つの式の値を別の値で除算して剰余を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
result = number1 % number2  
```  
  
## <a name="arguments"></a>引数  
 `result`  
 任意の変数。  
  
 `number1`  
 任意の数式。  
  
 `number2`  
 任意の数式。  
  
## <a name="remarks"></a>コメント  
 除算の剰余演算子`number1`によって`number2`として剰余のみを返します`result`です。 符号`result`の符号と同じ`number1`です。 値`result`は 0 ~ の絶対値`number2`です。  
  
 次のコードでは、剰余演算子を使用する方法を示します。  
  
```  
var modResult = 19 % 6.7;  
document.write(modResult);  
  
// Output: 5.6  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)
