---
title: Math オブジェクト (JavaScript) |Microsoft ドキュメント
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
- Math object
ms.assetid: 607b94cb-921c-43cd-b514-fdbc13aeced6
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f16fe4edf6a2a49db15d74abc8ebe6e53f955710
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24642162"
---
# <a name="math-object-javascript"></a>Math オブジェクト (JavaScript)
数値計算のための基本的な演算機能と定数を提供する組み込みオブジェクトです。  
  
## <a name="syntax"></a>構文  
  
```  
  
Math.[{property | method}]  
```  
  
## <a name="parameters"></a>パラメーター  
 *プロパティ*  
 必須です。 プロパティのいずれかの名前、 **Math**です。 オブジェクト。  
  
 *メソッド*  
 必須です。 メソッドのいずれかの名前、 **Math**です。 オブジェクト。  
  
## <a name="remarks"></a>コメント  
 **Math**を使用してオブジェクトを作成することはできません、**新しい**演算子、エラーとなりますようにしようとするとします。 このオブジェクトは、スクリプト エンジンにより、エンジンが読み込まれるときに作成されます。 これらのメソッドとプロパティすべては、いつでもスクリプトで使用できます。  
  
## <a name="requirements"></a>要件  
 `Math` オブジェクトは、[!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)] で導入されました。  
  
<a name="js56jsobjmathprop"></a>   
## <a name="constants"></a>定数  
 `Math` オブジェクトの定数を次の表に示します。  
  
|定数|説明|  
|--------------|-----------------|  
|[Math.E 定数](../../javascript/reference/math-constants-javascript.md)|数学定数 e。 オイラー数、自然対数の底です。|  
|[Math.LN2 定数](../../javascript/reference/math-constants-javascript.md)|2 の自然対数。|  
|[Math.LN10 定数](../../javascript/reference/math-constants-javascript.md)|10 の自然対数。|  
|[Math.LOG2E 定数](../../javascript/reference/math-constants-javascript.md)|2 を底とする e の対数。|  
|[Math.LOG10E 定数](../../javascript/reference/math-constants-javascript.md)|10 を底とする e の対数。|  
|[Math.PI 定数](../../javascript/reference/math-constants-javascript.md)|Pi。 円周率です。|  
|[Math.SQRT1_2 定数](../../javascript/reference/math-constants-javascript.md)|0.5 の平方根、または 1 を 2 の平方根で除算しても同じです。|  
|[Math.SQRT2 定数](../../javascript/reference/math-constants-javascript.md)|2 の平方根。|  
  
<a name="js56jsobjmathmeth"></a>   
## <a name="functions"></a>関数  
 `Math` オブジェクトの関数を次の表に示します。  
  
|関数|説明|  
|--------------|-----------------|  
|[Math.abs 関数](../../javascript/reference/math-abs-function-javascript.md)|絶対値を返します。|  
|[Math.acos 関数](../../javascript/reference/math-acos-function-javascript.md)|アークコサイン (逆余弦) を返します。|  
|[Math.acosh 関数](../../javascript/reference/math-acosh-function-javascript.md)|数値のハイパーボリック アークコサイン (または逆ハイパーボリック コサイン) を返します。|  
|[Math.asin 関数](../../javascript/reference/math-asin-function-javascript.md)|アークサイン (逆正弦) を返します。|  
|[Math.asinh 関数](../../javascript/reference/math-asinh-function-javascript.md)|数値の逆ハイパーボリック サインを返します。|  
|[Math.atan 関数](../../javascript/reference/math-atan-function-javascript.md)|アークタンジェント (逆正接) を返します。|  
|[Math.atan2 関数](../../javascript/reference/math-atan2-function-javascript.md)|X 軸から、提供された (X,Y) 座標が示す点への角度を、ラジアン単位で返します。|  
|[Math.atanh 関数](../../javascript/reference/math-atanh-function-javascript.md)|数値の逆ハイパーボリック タンジェントを返します。|  
|[Math.ceil 関数](../../javascript/reference/math-ceil-function-javascript.md)|提供された数式以上の、最小の整数を返します。|  
|[Math.cos 関数](../../javascript/reference/math-cos-function-javascript.md)|コサイン (余弦) を返します。|  
|[Math.cosh 関数](../../javascript/reference/math-cosh-function-javascript.md)|数値のハイパーボリック コサインを返します。|  
|[Math.exp 関数](../../javascript/reference/math-exp-function-javascript.md)|返します*e*累乗 (自然対数の底)。|  
|[Math.expm1 関数](../../javascript/reference/math-expm1-function-javascript.md)|e (自然対数の底) を指数で累乗した値から 1 を減算した結果を返します。|  
|[Math.floor 関数](../../javascript/reference/math-floor-function-javascript.md)|提供された数式以下の、最大の整数を返します。|  
|[Math.hypot 関数](../../javascript/reference/math-hypot-function-javascript.md)|引数の二乗の和の平方根を返します。|  
|[Math.imul 関数](../../javascript/reference/math-imul-function-javascript.md)|32 ビットの符号付き整数として扱われる 2 つの数値の積を返します。|  
|[Math.log 関数](../../javascript/reference/math-log-function-javascript.md)|自然対数を返します。|  
|[Math.log1p 関数](../../javascript/reference/math-log1p-function-javascript.md)|1 + 数値の自然対数を返します。|  
|[Math.log10 関数](../../javascript/reference/math-log10-function-javascript.md)|数値の底 10 の対数を返します。|  
|[Math.log2 関数](../../javascript/reference/math-log2-function-javascript.md)|数値の底 2 の対数を返します。|  
|[Math.max 関数](../../javascript/reference/math-max-function-javascript.md)|2 つの提供された数式から大きい方の値を返します。|  
|[Math.min 関数](../../javascript/reference/math-min-function-javascript.md)|2 つの提供された数式から小さい方の値を返します。|  
|[Math.pow 関数](../../javascript/reference/math-pow-function-javascript.md)|底の式を指定の数値でべき乗した値を返します。|  
|[Math.random 関数](../../javascript/reference/math-random-function-javascript.md)|0 ～ 1 間の疑似乱数を返します。|  
|[Math.round 関数](../../javascript/reference/math-round-function-javascript.md)|指定の数式を最も近い整数に丸めて返します。|  
|[Math.sign 関数](../../javascript/reference/math-sign-function-javascript.md)|数値が正、負、または 0 のいずれであるかを示す、数値の符号を返します。|  
|[Math.sin 関数](../../javascript/reference/math-sin-function-javascript.md)|サイン (正弦) を返します。|  
|[Math.sinh 関数](../../javascript/reference/math-sinh-function-javascript.md)|数値の逆ハイパーボリック サインを返します。|  
|[Math.sqrt 関数](../../javascript/reference/math-sqrt-function-javascript.md)|平方根を返します。|  
|[Math.tan 関数](../../javascript/reference/math-tan-function-javascript.md)|タンジェント (正接) を返します。|  
|[Math.tanh 関数](../../javascript/reference/math-tanh-function-javascript.md)|数値のハイパーボリック タンジェントを返します。|  
|[Math.trunc 関数](../../javascript/reference/math-trunc-function-javascript.md)|数値の小数部の桁を除去して、整数部分を返します。|  
  
## <a name="see-also"></a>関連項目  
 [JavaScript オブジェクト](../../javascript/reference/javascript-objects.md)   
 [Number オブジェクト](../../javascript/reference/number-object-javascript.md)