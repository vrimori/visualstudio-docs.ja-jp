---
title: "符号なし右シフト代入演算子 (&gt;&gt;&gt;=) (JavaScript) |Microsoft ドキュメント"
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
- '>>>='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>>>= operator'
- unsigned right shift assignment operator (>>>=)
- assignment operators, JavaScript
ms.assetid: f67c3737-7d39-41ae-9c11-8b16d38f6179
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1272cbb58645df605743c6790642cd0e295442aa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="unsigned-right-shift-assignment-operator-gtgtgt-javascript"></a>符号なし右シフト代入演算子 (&gt;&gt;&gt;=) (JavaScript)
式の値で指定されたビット数だけ変数の値を右にシフトし、符号は保持しないで、その結果を変数に代入します。  
  
## <a name="syntax"></a>構文  
  
```  
  
result >>>= expression  
```  
  
## <a name="parameters"></a>パラメーター  
 *結果*  
 任意の変数。  
  
 *式*  
 任意の式。  
  
## <a name="remarks"></a>コメント  
 使用して、>>> = 演算子は、以下の手順と同じでは正確にします。  
  
```JavaScript  
result = result >>> expression  
```  
  
 **>>>=** 演算子は、の各ビットをシフト*結果*で指定されたビット数だけ右*式*です。 ゼロは、左からに入力されます。 右側の外に移動桁は破棄されます。 例:  
  
```JavaScript  
var temp  
temp = -14  
temp >>>= 2  
```  
  
 変数*temp* -14 (2 の補数バイナリで 11111111 11111111 11111111 11110010) の初期値が含まれています。 右に 2 ビットをシフトしたときに、値は 1073741820 (で 00111111 11111111 11111111 11111100)。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [符号なし右シフト演算子 (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [ビットごとの左シフト演算子 (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [ビットごとの右シフト演算子 (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)