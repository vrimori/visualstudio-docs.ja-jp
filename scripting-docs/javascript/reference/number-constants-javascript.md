---
title: "Number 定数 (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- POSITIVE_INFINITY constant [JavaScript]
- MAX_VALUE constant [JavaScript]
- MIN_VALUE constant [JavaScript]
- number constants [JavaScript]
- Number.NEGATIVE_INFINITY constant [JavaScript]
- Number.POSITIVE_INFINITY constant [JavaScript]
- NEGATIVE_INFINITY constant [JavaScript]
- NaN constant [JavaScript]
- Number.MIN_VALUE constant [JavaScript]
- constants [JavaScript], number
- Number.NaN constant [JavaScript]
- Number.MAX_VALUE constant [JavaScript]
ms.assetid: e0701b41-99ae-4916-9ec0-f79bb15386fb
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f846ef7cbd9609f7913d6305e48cb4942476ca21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="number-constants-javascript"></a>Number 定数 (JavaScript)
次の数値定数は、`Number` オブジェクトのプロパティです。  
  
## <a name="number-object-constants"></a>数値オブジェクト定数  
 これらの定数にアクセスするために `Number` オブジェクトを作成する必要はありません。  
  
|定数|返される値|  
|--------------|--------------------|  
|`Number.EPSILON`|[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] で表せる最小の数値。 約 2.2204460492503130808472633361816E-16。|  
|`Number.MAX_SAFE_INTEGER`|JavaScript で安全に表現できる最大の数値。 9007199254740991 と等価です。|  
|`Number.MAX_VALUE`|[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] で表せる最大の数値。 約 1.79E+308。|  
|`Number.MIN_SAFE_INTEGER`|JavaScript で安全に表現できる最小の数値。 -9007199254740991 等しい。|  
|`Number.MIN_VALUE`|[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] で表せるゼロに最も近い数値。 約 5.00E-324。|  
|`Number.NaN`|数値以外の値<br /><br /> 等価比較では、`NaN` は、それ自体を含めいずれの値とも等しくありません。 値が等価かどうかをテストする`NaN`を使用して、 [isNaN 関数](../../javascript/reference/isnan-function-javascript.md)です。|  
|`Number.NEGATIVE_INFINITY`|[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] で表せる負の最大数値より小さい値。<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] は、`NEGATIVE_INFINITY` 値を `-infinity` として表示します。|  
|`Number.POSITIVE_INFINITY`|[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] で表せる最大数値より大きい値。<br /><br /> [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] は、`POSITIVE_INFINITY` 値を `infinity` として表示します。|  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 `Number.EPSILON`、`Number.MAX_SAFE_INTEGER`、および `Number.MIN_SAFE_INTEGER` の場合:  
  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **適用されます**:[オブジェクトの数](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [数値演算定数](../../javascript/reference/math-constants-javascript.md)   
 [JavaScript 定数](../../javascript/reference/javascript-constants.md)   
 [定数 infinity](../../javascript/reference/infinity-constant-javascript.md)   
 [NaN 定数](../../javascript/reference/nan-constant-javascript.md)   
 [isNaN 関数](../../javascript/reference/isnan-function-javascript.md)