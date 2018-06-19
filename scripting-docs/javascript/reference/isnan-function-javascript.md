---
title: isNaN 関数 (JavaScript) |Microsoft ドキュメント
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
- isNaN
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- isNaN method
ms.assetid: 5af4eb29-72f6-484f-93bd-04ae1261f849
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7b7e6d3687e795ea5d5e38308a8af0d73ba7f5ff
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637622"
---
# <a name="isnan-function-javascript"></a>isNaN 関数 (JavaScript)
値が予約済みの値 `NaN` (非数) であるかどうかを示すブール値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
isNaN(numValue)   
```  
  
## <a name="return-value"></a>戻り値  
 `Number` 型に変換される値が `NaN` の場合は `true`、それ以外の場合は `false`。  
  
## <a name="remarks"></a>コメント  
 必要な`numValue`に対してテストする値は、`NaN`です。  
  
 このメソッドは、通常は `parseInt` と `parseFloat` メソッドからの戻り値をテストするために使用します。  
  
 含む変数または、`NaN`か、別の値をそれ自体に比較可能性があります。 等しくない場合、`NaN`です。 これは、ため`NaN`自体にではない唯一の値です。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用されます**:[グローバル オブジェクト](../../javascript/reference/global-object-javascript.md)  
  
## <a name="example"></a>例  
  
```JavaScript  
// Returns false.  
isNaN(100);  
  
// Returns false.  
isNaN("100");  
  
// Returns true.  
isNaN("ABC");  
  
// Returns true.  
isNaN("10C");  
  
// Returns true.  
isNaN("abc123");  
  
// Returns true.  
isNaN(Math.sqrt(-1));           
```  
  
## <a name="see-also"></a>関連項目  
 [isFinite 関数](../../javascript/reference/isfinite-function-javascript.md)   
 [NaN 定数](../../javascript/reference/nan-constant-javascript.md)   
 [parseFloat 関数](../../javascript/reference/parsefloat-function-javascript.md)   
 [parseInt 関数](../../javascript/reference/parseint-function-javascript.md)