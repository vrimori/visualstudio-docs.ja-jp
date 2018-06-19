---
title: Math.clz32 関数 (JavaScript) |Microsoft ドキュメント
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
ms.assetid: 34615d7a-6d88-4ab5-a696-7e496caa51db
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 511f407acc327a32ed6c53c12283503e20b514fe
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638082"
---
# <a name="mathclz32-function-javascript"></a>Math.clz32 関数 (JavaScript)
32 ビットのバイナリ表記の数値における先行ゼロのビット数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Math.clz32(  
number  
)   
```  
  
## <a name="remarks"></a>コメント  
 `number` が 0 の場合、結果は 32 になります。 `number` の 32 ビットのバイナリ エンコーディングの最上位ビットが 1 の場合、結果は 0 になります。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **適用されます**: [Math オブジェクト](../../javascript/reference/math-object-javascript.md)