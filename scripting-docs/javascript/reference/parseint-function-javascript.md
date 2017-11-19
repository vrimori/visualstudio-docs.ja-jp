---
title: "parseInt 関数 (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: parseInt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: parseInt method
ms.assetid: e86471af-2a0e-4359-83af-f1ac81e51421
caps.latest.revision: "24"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 54ee77470d32410ae46a628d54fc3bda97fecc51
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="parseint-function-javascript"></a>parseInt 関数 (JavaScript)
文字列を整数に変換します。  
  
## <a name="syntax"></a>構文  
  
```  
parseInt(numString, [radix])   
```  
  
## <a name="parameters"></a>パラメーター  
 `numString`  
 必須です。 数値に変換する文字列。  
  
 `radix`  
 省略可能です。 2 ~ 36 の数値の基数を指定する値`numString`です。 この引数が指定されていない場合は、'0 x' のプレフィックスを持つ文字列が 16 進数と見なされます。 その他のすべての文字列は、10 進数と見なされます。  
  
## <a name="remarks"></a>コメント  
 `parseInt`関数に含まれている値に等しい整数値を返します`numString`です。 場合のプレフィックスなし`numString`、整数型に正常に解析された`NaN`(非数) が返されます。  
  
```JavaScript  
parseInt("abc");     // Returns NaN.  
parseInt("12abc");   // Returns 12.  
```  
  
 テストできます`NaN`を使用して、`isNaN`関数。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用されます**:[グローバル オブジェクト](../../javascript/reference/global-object-javascript.md)  
  
> [!NOTE]
>  以降で[!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)]、`parseInt`関数は、8 進数として '0' のプレフィックスを持つ文字列を処理しません。 使用しない場合、`parseInt`機能は、ただし、'0' のプレフィックスを持つ文字列依然として解釈できるからです。 参照してください[データ型](../../javascript/data-types-javascript.md)については、8 進整数。  
  
## <a name="see-also"></a>関連項目  
 [isNaN 関数](../../javascript/reference/isnan-function-javascript.md)   
 [parseFloat 関数](../../javascript/reference/parsefloat-function-javascript.md)   
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)   
 [valueOf メソッド (Object)](../../javascript/reference/valueof-method-object-javascript.md)