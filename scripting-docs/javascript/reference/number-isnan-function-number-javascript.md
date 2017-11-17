---
title: "Number.isNaN 関数 (Number) (JavaScript) |Microsoft ドキュメント"
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
ms.assetid: 2d9813d6-ec9c-433b-b060-8e3c3ff62ca4
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c11abe2dd2fc70431800d31f4c44279a88cd75d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="numberisnan-function-number-javascript"></a>Number.isNaN 関数 (Number) (JavaScript)
値が予約済みの値 `NaN` (非数) であるかどうかを示すブール値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
Number.isNaN(numValue)   
```  
  
#### <a name="parameters"></a>パラメーター  
 `numValue`  
 必須です。 `NaN` に対してテストする値。  
  
## <a name="return-value"></a>戻り値  
 `Number` 型に変換される値が `NaN` の場合は `true`、それ以外の場合は `false`。  
  
## <a name="remarks"></a>コメント  
 このメソッドは、通常は `parseInt` と `parseFloat` メソッドからの戻り値をテストするために使用します。  
  
 `Number.isNaN` は、グローバル `isNaN` 関数の問題を修正します。  `Number.isNaN` は、`NaN` と比較した後にのみ、その引数を Number 型に変換します。 そのため、`true` が返されるのは、渡された引数が `NaN` とまったく同じ値である場合に限定されます。 グローバル `isNaN` 関数は、比較の前に引数を Number 型に変換するので、非数値によって `true` が返されることがある一方で、`Number.isNaN` に対して `true` が返されないこともあります。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]  
  
 **適用されます**:[オブジェクトの数](../../javascript/reference/number-object-javascript.md)  
  
## <a name="example"></a>例  
  
```JavaScript  
// Returns true.  
Number.isNaN(NaN);  
Number.isNaN(Number.NaN);  
Number.isNaN(0 / 0);  
  
// Returns false.  
Number.isNaN(100);  
// Returns false.  
// Strings are converted to numbers and return false.  
Number.isNaN("100");  
Number.isNaN("ABC");  
Number.isNaN("10C");  
Number.isNaN("abc123");  
  
```