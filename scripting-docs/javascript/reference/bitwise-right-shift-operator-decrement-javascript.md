---
title: "ビットごとの右シフト演算子 (&gt;&gt;) (JavaScript) |Microsoft ドキュメント"
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
- '>>'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>> operator'
- '>> operator, about >> operator'
- '>> operator, bitsets'
- bitwise operators, right shift operator
ms.assetid: 89dc57e0-0b0d-49a4-a8ed-56d8bb20f3e3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 70db0c176b475886a26cfe4c06f7f2f0c9d4fc2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="bitwise-right-shift-operator-gtgt-javascript"></a>ビットごとの右シフト演算子 (&gt;&gt;) (JavaScript)
符号は保持、式のビットを右にシフトします。  
  
## <a name="syntax"></a>構文  
  
```  
  
result = expression1 >> expression2  
```  
  
## <a name="parameters"></a>パラメーター  
 *結果*  
 任意の変数。  
  
 *expression1*  
 任意の式。  
  
 *expression2*  
 任意の式。  
  
## <a name="remarks"></a>コメント  
 >> 演算子は、の各ビットをシフト*expression1*で指定されたビット数だけ右*expression2*です。 符号ビットの*expression1*左側の桁の数字の塗りつぶしに使用します。 右側の外に移動桁は破棄されます。 たとえば、次のコードが評価された後*temp* -4 の値を持つ:-14 (11110010 で 2 つのビットごとの補数バイナリ) 右に 2 ビット equals-4 (11111100 で 2 つのビットごとの補数バイナリ) にシフトします。  
  
```JavaScript  
var temp  
temp = -14 >> 2  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ビットごとの左シフト演算子 (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [右シフト代入演算子 (>> =)](../../javascript/reference/right-shift-assignment-operator-decrement-equal-javascript.md)   
 [符号なし右シフト演算子 (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)