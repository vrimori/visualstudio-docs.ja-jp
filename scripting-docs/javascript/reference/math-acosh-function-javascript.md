---
title: "Math.acosh 関数 (JavaScript) |Microsoft ドキュメント"
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
ms.assetid: 881dd2a0-36a5-403b-a3dc-523d8e1e1317
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1fd75140dfcf3d9ac703c2aeadf68bea4da9e0dc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="mathacosh-function-javascript"></a>Math.acosh 関数 (JavaScript)
数値のハイパーボリック アークコサイン (または逆ハイパーボリック コサイン) を返します。  
  
## <a name="syntax"></a>構文  
  
```  
Math.acosh(number)  
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な `number` 引数は、数値式です。  
  
## <a name="return-value"></a>戻り値  
 `number` 引数の逆ハイパーボリック コサインをラジアンで返します。  
  
## <a name="example"></a>例  
 次のコードは、`acosh` 関数の使用方法を示しています。  
  
```JavaScript  
var v1 = Math.acosh(3);  
vary v2 = Math.acosh(-1);  
  
document.write(v1);  
document.write("</br>");  
document.write(v2);  
  
// Output:  
// 1.762747174039086  
// NaN  
  
```  
  
## <a name="remarks"></a>コメント  
 **適用されます**: [Math オブジェクト](../../javascript/reference/math-object-javascript.md)  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Math.acos 関数](../../javascript/reference/math-acos-function-javascript.md)   
 [Math.asin 関数](../../javascript/reference/math-asin-function-javascript.md)   
 [Math.atan 関数](../../javascript/reference/math-atan-function-javascript.md)   
 [Math.cos 関数](../../javascript/reference/math-cos-function-javascript.md)   
 [Math.sin 関数](../../javascript/reference/math-sin-function-javascript.md)   
 [Math.tan 関数](../../javascript/reference/math-tan-function-javascript.md)   
 [Math オブジェクト](../../javascript/reference/math-object-javascript.md)