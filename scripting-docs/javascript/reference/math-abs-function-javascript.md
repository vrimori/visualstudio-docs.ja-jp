---
title: Math.abs 関数 (JavaScript) |Microsoft ドキュメント
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
- abs
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- absolute values, calculating
- absolute values
- numeric expressions
- abs method
ms.assetid: 9af4b5b8-de77-47bb-bb59-abdde371e4c3
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5719905a7de375f1b409378f0579e3d8b25209fc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638372"
---
# <a name="mathabs-function-javascript"></a>Math.abs 関数 (JavaScript)
(正と負の値であるかに関係なく値) の数値の絶対値を返します。 たとえば、-5 の絶対値は、5 の絶対値と同じです。  
  
## <a name="syntax"></a>構文  
  
```  
Math.abs(number)  
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な`number`引数は、絶対値を必要とする数値式です。  
  
## <a name="return-value"></a>戻り値  
 絶対値、`number`引数。  
  
## <a name="example"></a>例  
 `abs` 関数の使用例を次に示します。  
  
```JavaScript  
var s;  
var v1 = Math.abs(6);  
var v2 = Math.abs(-6);  
if (v1 == v2) {  
    document.write("Absolute values are the same.");  
}  
else {  
document.write("Absolute values are different.");  
}  
  
// Output: Absolute values are the same.  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用されます**: [Math オブジェクト](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [Math オブジェクト](../../javascript/reference/math-object-javascript.md)