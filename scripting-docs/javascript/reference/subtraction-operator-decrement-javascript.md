---
title: "減算演算子 (-) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '-'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '- operator, about - operator'
- '- operator'
- negation operator
- subtraction operator, syntax
- arithmetic operators, subtraction
- operators, subtraction
ms.assetid: cd0681d3-15cd-49fe-b4dd-e087de55d778
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fb79aab0a57c733871dbfc73ac96c7ddbf4db37c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="subtraction-operator---javascript"></a>減算演算子 (-) (JavaScript)
別の 1 つの式の値を減算または 1 つの式の単項否定演算を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
  
result = number1 - number2;  
```  
  
## <a name="parameters"></a>パラメーター  
 *結果*  
 任意の数値変数です。  
  
 `number`  
 任意の数式。  
  
 `number1`  
 任意の数式。  
  
 `number2`  
 任意の数式。  
  
## <a name="remarks"></a>コメント  
 構文 1、  **-** 演算子は、次の 2 つの数値の差を見つけるために使用する算術減算演算子。 構文 2 では、  **-** 演算子は単項否定演算子、式の負の値を示すために使用します。  
  
 構文 2 では、すべての単項演算子と式には、次のように。  
  
-   未定義に適用される場合または`null`式、実行時エラーが発生します。  
  
-   オブジェクトは、文字列に変換されます。  
  
-   文字列は、可能な場合は数値に変換されます。 それ以外の場合は、実行時エラーが発生しました。  
  
-   ブール値は、数字 (0 false の場合、true の場合は 1) として扱われます。  
  
 演算子は、結果の数に適用されます。 結果の数が 0 でない場合、構文 2 で*結果*が符号を反転させたと結果の数と等しい。 結果の数が 0 の場合*結果*は 0 です。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [減算代入演算子 (-)](../../javascript/reference/subtraction-assignment-operator-decrement-equal-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)