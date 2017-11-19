---
title: "加算代入演算子 (+ =) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: +=
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- addition assignment operator (+=)
- += operator
- assignment operators, JavaScript
ms.assetid: 8517d05c-38b0-4107-bea4-253eb420f438
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 38d86c537dda90dd7f44923b97384b3609dad5ba
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="addition-assignment-operator--javascript"></a>加算代入演算子 (+=) (JavaScript)
変数の値に式の値を追加し、その結果を変数に代入します。  
  
## <a name="syntax"></a>構文  
  
```  
  
result += expression   
```  
  
## <a name="parameters"></a>パラメーター  
 `result`  
 任意の変数。  
  
 `expression`  
 任意の式。  
  
## <a name="remarks"></a>コメント  
 この演算子を使ってまったく同じであるを指定すると:`result = result + expression`です。  
  
 2 つの式の種類の動作を決定する、`+=`演算子。  
  
|If|Then|  
|--------|----------|  
|両方の式は数値またはブール値|追加|  
|両方の式が文字列|連結|  
|1 つの式が数値で、もう一方の文字列|連結|  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [加算演算子 (+)](../../javascript/reference/addition-operator-decrement-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)