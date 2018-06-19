---
title: 数値演算定数 (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- LN2 constant [JavaScript]
- E constant [JavaScript]
- LOG10E constant [JavaScript]
- SQRT1_2 constant [JavaScript]
- LOG2E constant [JavaScript]
- Math.SQRT2 constant [JavaScript]
- PI constant [JavaScript]
- Math.LOG2E constant [JavaScript]
- constants [JavaScript], math
- Math.E constant [JavaScript]
- logarithm consants [JavaScript]
- Math.LOG10E constant [JavaScript]
- Math.SQRT1_2 constant [JavaScript]
- SQRT2 constant [JavaScript]
- square root constants [JavaScript]
- Math.PI constant [JavaScript]
- math constants [JavaScript]
- LN10 constant [JavaScript]
- Math.LN2 constant [JavaScript]
- Math.LN10 constant [JavaScript]
ms.assetid: 8a674046-cb99-4103-92be-83697fba6344
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9942abb69af416cd4cd7f092dc9f1478e0bc3a69
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638952"
---
# <a name="math-constants-javascript"></a>数値演算定数 (JavaScript)
数値演算定数は、のプロパティを定数値を返す、`Math`オブジェクト。  
  
## <a name="math-object-constants"></a>Math オブジェクトの定数  
 次の表のプロパティを定数値、 [Math オブジェクト](../../javascript/reference/math-object-javascript.md)です。  
  
|定数|説明|概算値|  
|--------------|-----------------|-----------------------|  
|`Math.E`|数学定数 e。 オイラー数、自然対数の底です。|2.718|  
|`Math.LN2`|2 の自然対数。|0.693|  
|`Math.LN10`|10 の自然対数。|2.302|  
|`Math.LOG2E`|2 を底とする e の対数。|1.443|  
|`Math.LOG10E`|10 を底とする e の対数。|0.434|  
|`Math.PI`|Pi。 円周率です。|3.14159|  
|`Math.SQRT1_2`|0.5 の平方根、または 1 を 2 の平方根で除算しても同じです。|0.707|  
|`Math.SQRT2`|2 の平方根。|1.414|  
  
## <a name="example"></a>例  
 次の例を使用する方法を示しています、`Math.PI`定数。  
  
```JavaScript  
var radius = 3;  
var area = Math.PI * radius * radius;  
document.write(area);  
  
// Output: 28.274333882308138  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用されます**: [Math オブジェクト](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [数値定数](../../javascript/reference/number-constants-javascript.md)   
 [JavaScript 定数](../../javascript/reference/javascript-constants.md)