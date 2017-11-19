---
title: "isFinite 関数 (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: isFinite
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- finite numbers
- isFinite method
ms.assetid: ea9287d2-892f-496b-86b7-f9196868d5cf
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce78afe59190a03fb079841e7691f84c01eebedd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="isfinite-function-javascript"></a>isFinite 関数 (JavaScript)
指定した数値が有限かどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```  
isFinite(number)   
```  
  
## <a name="remarks"></a>コメント  
 必要な`number`引数が任意の数値。  
  
 `isFinite`関数が返される`true`場合`number`以外の任意の値は、 `NaN`、負の無限大、または正の無限大します。 これら 3 つのケースで返します**false**です。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用されます**:[グローバル オブジェクト](../../javascript/reference/global-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [isNaN 関数](../../javascript/reference/isnan-function-javascript.md)