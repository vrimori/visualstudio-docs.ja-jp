---
title: "callee プロパティ (arguments) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- callee
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- callee property
ms.assetid: ad9d4d21-73f0-44f6-8bec-502f3456cd23
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33f1c2926d76c0a1f088c8f4222b6f24c004b73b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="callee-property-arguments-javascript"></a>callee プロパティ (arguments) (JavaScript)
返します、`Function`オブジェクトの実行中、つまり、指定した本文`Function`オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
[function.]arguments.callee  
```  
  
## <a name="remarks"></a>コメント  
 省略可能な*関数*引数は、現在実行中の名前`Function`オブジェクト。  
  
 `callee`プロパティのメンバーである、**引数**関連付けられた関数を実行するときにのみを使用可能になったオブジェクトです。  
  
 初期値、`callee`プロパティは、`Function`実行されているオブジェクトします。 これにより、匿名の関数を再帰的です。  
  
## <a name="example"></a>例  
  
```JavaScript  
function factorial(n){  
  if (n <= 0)  
     return 1;  
  else  
     return n * arguments.callee(n - 1)  
}  
document.write(factorial(4));  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用先**:[引数オブジェクト](../../javascript/reference/arguments-object-javascript.md)&#124;です。[関数オブジェクト](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [caller プロパティ (Function)](../../javascript/reference/caller-property-function-javascript.md)