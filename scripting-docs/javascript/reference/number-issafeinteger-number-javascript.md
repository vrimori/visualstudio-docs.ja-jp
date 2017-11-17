---
title: "Number.isSafeInteger (Number) (JavaScript) |Microsoft ドキュメント"
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
ms.assetid: c7ef6ce8-fe71-4e53-be44-4dd440aef21d
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eebc2147bc5043341be7e883548af825922036f9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="numberissafeinteger-number-javascript"></a>Number.isSafeInteger (Number) (JavaScript)
JavaScript で数値を安全に表現できるかどうかを示すブール値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
Number.isSafeInteger(numValue)   
```  
  
## <a name="return-value"></a>戻り値  
 数値が `Number.MIN_SAFE_INTEGER` と `Number.MAX_SAFE_INTEGER` の間である場合 (その数値である場合も含む) は `true`、そうでない場合は `false`。  
  
## <a name="remarks"></a>コメント  
 JavaScript での安全な整数は、なんらかの丸め処理が適用される前に IEEE 754 倍精度数であるものです。  
  
## <a name="example"></a>例  
  
```JavaScript  
// Returns true  
Number.isSafeInteger(-100)  
Number.isSafeInteger(9007199254740991)  
  
// Returns false  
Number.isSafeInteger(Number.NaN)  
Number.isSafeInteger(Infinity)  
Number.isSafeInteger("100")  
Number.isSafeInteger(9007199254740992);  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **適用されます**:[オブジェクトの数](../../javascript/reference/number-object-javascript.md)