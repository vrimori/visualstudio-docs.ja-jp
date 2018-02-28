---
title: "Math.log 関数 (JavaScript) |Microsoft ドキュメント"
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
- log
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- log method
- Math object
ms.assetid: 5d617fb5-4b27-404e-842f-eea5549a7c1a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62bfb6bf9bb95b541a51224af4484ded22ccb4e8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="mathlog-function-javascript"></a>Math.log 関数 (JavaScript)
自然対数を返します (基本`e`) の数値。  
  
## <a name="syntax"></a>構文  
  
```  
Math.log(number)   
```  
  
#### <a name="parameters"></a>パラメーター  
 number  
 数値。  
  
## <a name="return-value"></a>戻り値  
 場合`number`が正の値であり、この関数は、数値の自然対数を返します。 場合`number`は負の値を返します`NaN`です。 場合`number`0 の場合は、この関数が返される`-Infinity`です。  
  
## <a name="example"></a>例  
 次のコードでは、この関数を使用する方法を示します。  
  
```JavaScript  
var numArr = [ 45.3, 69.0, 557.04, 0.222 ];  
  
for (i in numArr) {  
    document.write(Math.log(numArr[i]));  
    document.write("<br/>");  
}  
  
// Output:   
// 3.8133070324889884  
// 4.23410650459726  
// 6.322637050634291  
// -1.5050778971098575  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用されます**: [Math オブジェクト](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [Math.sqrt 関数](../../javascript/reference/math-sqrt-function-javascript.md)