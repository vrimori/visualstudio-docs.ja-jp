---
title: "Array.of 関数 (Array) (JavaScript) |Microsoft ドキュメント"
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
ms.assetid: 2884dda3-65d1-4990-9afe-87865c2d4f7f
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 042315bbc3b956e92fff866f7d403b6f87726a74
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="arrayof-function-array-javascript"></a>Array.of 関数 (Array) (JavaScript)
引数として渡されたものから配列を返します。  
  
## <a name="syntax"></a>構文  
  
```  
Array.of(element0[, element1][, ...][,elementN]);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `element0,...,elementN`  
 省略可能です。 配列に代入する要素を指定します。 これにより、要素数が n + 1、長さが n + 1 の配列が作成されます。  
  
## <a name="remarks"></a>コメント  
 この関数は `new Array(args)` の呼び出しに似ていますが、`Array.of` では 1 つの引数が渡されたときに、特別な処理は行われません。  
  
## <a name="example"></a>例  
 次の例では、渡された数値から配列を作成します。  
  
```JavaScript  
var arr = Array.of(1, 2, 3);  
// arr[0] == 1   
```  
  
## <a name="example"></a>例  
 次の例では、`Array.of` と `new Array` の使用方法の違いを示しています。  
  
```JavaScript  
var arr1 = Array.of(3);  
// arr1[0] == 3  
  
// With new Array, a single argument specifies  
// the length of the new array.  
var arr2 = new Array(3);  
// arr2[0] is undefined  
// arr2.length == 3  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]