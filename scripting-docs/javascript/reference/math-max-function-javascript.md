---
title: "Math.max 関数 (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: max
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: max method
ms.assetid: f3ea1b8a-5fd0-482a-971b-b7f8e2b9b7eb
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: adf66164346f3802d92f8e0de82356df49bad5fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="mathmax-function-javascript"></a>Math.max 関数 (JavaScript)
指定された数値式のセットのうち、大きい方を返します。  
  
## <a name="syntax"></a>構文  
  
```  
Math.max([number1[, number2[... [, numberN]]]])   
```  
  
## <a name="remarks"></a>コメント  
 省略可能な`number1, number2, ..., numberN`引数が評価される数値式です。  
  
 引数が指定されていない場合、戻り値は[Number.NEGATIVE_INFINITY](../../javascript/reference/number-constants-javascript.md)です。 場合、引数が`NaN`、戻り値も`NaN`します。  
  
## <a name="example"></a>例  
 次のコードは、2 つの式のうち、大きい方を取得する方法を示しています。  
  
```JavaScript  
var x = Math.max(107 - 3,  48 * 90);  
document.write(x);  
  
// Output:  
// 4320  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Math.min 関数](../../javascript/reference/math-min-function-javascript.md)