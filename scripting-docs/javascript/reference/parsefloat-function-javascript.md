---
title: "parseFloat 関数 (JavaScript) |Microsoft ドキュメント"
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
- parseFloat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- parseFloat method
ms.assetid: a7d87a69-1919-4623-be85-972e6376dd2d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eb8f6d179abba887542e59d083141534732ed42a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="parsefloat-function-javascript"></a>parseFloat 関数 (JavaScript)
文字列を浮動小数点数に変換します。  
  
## <a name="syntax"></a>構文  
  
```  
parseFloat(numString)   
```  
  
## <a name="remarks"></a>コメント  
 必要な`numString`引数は浮動小数点数値を含んだ文字列。  
  
 `parseFloat`値を返します、数値で格納された数値と等しい`numString`です。 場合のプレフィックスなし`numString`浮動小数点数に正常に解析された`NaN`(非数) が返されます。  
  
```JavaScript  
parseFloat("abc")      // Returns NaN.  
parseFloat("1.2abc")   // Returns 1.2.  
```  
  
 テストできます`NaN`を使用して、`isNaN`関数。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用されます**:[グローバル オブジェクト](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [isNaN 関数](../../javascript/reference/isnan-function-javascript.md)   
 [parseInt 関数](../../javascript/reference/parseint-function-javascript.md)   
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)