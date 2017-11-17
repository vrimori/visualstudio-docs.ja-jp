---
title: "Number.isFinite 関数 (Number) (JavaScript) |Microsoft ドキュメント"
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
ms.assetid: 41a91408-09d1-49f2-b7a0-6da105e2ed8e
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c23ff1e80ad71fd9d848f7a0e33628131f5d8014
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="numberisfinite-function-number-javascript"></a>Number.isFinite 関数 (Number) (JavaScript)
値が有限数であるかどうかを示すブール値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
Number.isFinite(numValue)   
```  
  
## <a name="return-value"></a>戻り値  
 値が `NaN`、`+∞`、または `-∞` の場合は `false`、それ以外の場合は `true`。  
  
## <a name="remarks"></a>コメント  
  
## <a name="example"></a>例  
  
```JavaScript  
// Returns true  
Number.isFinite(100)  
Number.isFinite(-100)  
Number.isFinite(100 / 3)  
  
// Returns false  
Number.isFinite(Number.NaN)  
Number.isFinite(Infinity)  
Number.isFinite("100")  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **適用されます**:[オブジェクトの数](../../javascript/reference/number-object-javascript.md)