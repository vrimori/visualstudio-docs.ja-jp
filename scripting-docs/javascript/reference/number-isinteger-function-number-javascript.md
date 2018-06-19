---
title: Number.isInteger 関数 (Number) (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 54fcf68c-0067-4bad-af94-d7ff8c88914a
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 20e1b7b463003d3a25ef64bba793b3273371266b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638802"
---
# <a name="numberisinteger-function-number-javascript"></a>Number.isInteger 関数 (Number) (JavaScript)
値が整数であるかどうかを示すブール値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
Number.isInteger(numValue)   
```  
  
## <a name="return-value"></a>戻り値  
 値が整数である場合は `true` を返します。それ以外の場合は `false` を返します。  
  
## <a name="remarks"></a>コメント  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **適用されます**:[オブジェクトの数](../../javascript/reference/number-object-javascript.md)  
  
## <a name="example"></a>例  
  
```JavaScript  
// Returns true  
Number.isInteger(100)  
Number.isInteger(-100)  
  
// Returns false  
Number.isInteger(Number.NaN)  
Number.isInteger(Infinity)  
Number.isInteger(100 / 3)  
Number.isInteger("100")  
  
```