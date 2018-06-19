---
title: 加算演算子 (+) (JavaScript) |Microsoft ドキュメント
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
- +
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arithmetic operators, addition
- strings [Visual Studio], concatenating
- concatenation operators, vs. addition operator
- addition operator
- + operator
ms.assetid: ec1237d3-e78b-4e77-bd7d-c0204cf03acd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70ff02b1f234da7b88d28e66da82262ccef7bfaf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633262"
---
# <a name="addition-operator--javascript"></a>加算演算子 (+) (JavaScript)
間、1 つの数値式の値を追加または 2 つの文字列を連結します。  
  
## <a name="syntax"></a>構文  
  
```  
  
result = expression1 + expression2  
```  
  
## <a name="parameters"></a>パラメーター  
 `result`  
 任意の変数。  
  
 `expression1`  
 任意の式。  
  
 `expression2`  
 任意の式。  
  
## <a name="remarks"></a>コメント  
 2 つの式の種類の動作を決定する、  **+** 演算子。  
  
|If|Then|  
|--------|----------|  
|両方の式は数値またはブール値|追加|  
|両方の式が文字列|連結|  
|1 つの式が数値で、もう一方の文字列|連結|  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [加算代入演算子 (+ =)](../../javascript/reference/addition-assignment-operator-decrement-equal-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)