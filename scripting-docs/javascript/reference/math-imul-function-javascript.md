---
title: Math.imul 関数 (JavaScript) |Microsoft ドキュメント
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
ms.assetid: dce5e11c-36b9-4c39-84d3-6cd494dd1cbf
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 57820d0926d574c75924f4eef6265ef7fa0766da
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638872"
---
# <a name="mathimul-function-javascript"></a>Math.imul 関数 (JavaScript)
32 ビットの符号付き整数として扱われる 2 つの数値の積を返します。  
  
## <a name="syntax"></a>構文  
  
```  
Math.imul(x, y);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `x`  
 必須です。 最初の数値。  
  
 `y`  
 必須です。 2 番目の数値。  
  
## <a name="remarks"></a>コメント  
 この関数は、JavaScript と同じ方法では整数の乗算を実装しない Emscripten や Mandreel などのコンパイラで使用されます。  
  
## <a name="example"></a>例  
 次のコード例では、`Math.imul` を使用して数値を乗算する方法を示しています。  
  
```JavaScript  
var result1 = Math.imul(2, 5);  
// result1 == 10  
  
var result2 = Math.imul(Math.pow(2, 32) - 1, Math.pow(2, 32) - 2);  
// result2 == 2   
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]