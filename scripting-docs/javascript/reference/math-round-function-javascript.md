---
title: Math.round 関数 (JavaScript) |Microsoft ドキュメント
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
- round
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Round method
- Math object
ms.assetid: 51008df3-5d0c-4951-84cb-4f41000db0be
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9543d529e3d0e4e45cff29f1286edbfad8dc0e27
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639192"
---
# <a name="mathround-function-javascript"></a>Math.round 関数 (JavaScript)
最も近い整数に丸められた、指定された数値式を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Math.round(  
number  
)   
```  
  
## <a name="remarks"></a>コメント  
 必要な`number`引数は、値を最も近い整数に丸められます。  
  
 、正の数値の場合の小数部分`number`0.5 以降を、戻り値がより大きい最小の整数と等しい`number`です。 小数部分が 0.5 未満の場合は、戻り値が最大の整数以下と等しい`number`です。  
  
 負の値、小数部分が完全にある場合、-0.5、戻り値は、数よりも大きい最小の整数。  
  
 たとえば、 `Math.round(8.5)` 9 を返しますが、 `Math.round(-8.5)` -8 を返します。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用されます**: [Math オブジェクト](../../javascript/reference/math-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [Math.random 関数](../../javascript/reference/math-random-function-javascript.md)