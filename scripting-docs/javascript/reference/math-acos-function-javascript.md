---
title: "Math.acos 関数 (JavaScript) |Microsoft ドキュメント"
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
- acos
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- acos method
- arcosine method
ms.assetid: 828cb3c3-bdf7-4bb7-97ae-3617ce4b2d62
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 773499287e215fbc161f289954811d3ef62bcba6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="mathacos-function-javascript"></a>Math.acos 関数 (JavaScript)
数値のアーク コサイン (または逆余弦) を返します。  
  
## <a name="syntax"></a>構文  
  
```  
Math.acos(number)  
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な `number` 引数は、数値式です。  
  
## <a name="return-value"></a>戻り値  
 アーク コサイン、`number`ラジアン単位での引数。  
  
## <a name="example"></a>例  
 次のコードは、`acos` 関数の使用方法を示しています。  
  
```JavaScript  
var v1 = Math.acos(-1.0);  
var v2 = Math.cos(-1.0);  
  
document.write(v1);  
document.write("<br/>");  
document.write(v2);  
  
// Output:  
// 3.141592653589793  
// 0.5403023058681398  
  
```  
  
## <a name="remarks"></a>コメント  
 **適用されます**: [Math オブジェクト](../../javascript/reference/math-object-javascript.md)  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Math.asin 関数](../../javascript/reference/math-asin-function-javascript.md)   
 [Math.atan 関数](../../javascript/reference/math-atan-function-javascript.md)   
 [Math.cos 関数](../../javascript/reference/math-cos-function-javascript.md)   
 [Math.sin 関数](../../javascript/reference/math-sin-function-javascript.md)   
 [Math.tan 関数](../../javascript/reference/math-tan-function-javascript.md)   
 [Math オブジェクト](../../javascript/reference/math-object-javascript.md)