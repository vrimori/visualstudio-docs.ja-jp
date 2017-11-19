---
title: "符号なし右シフト演算子 (&gt;&gt;&gt;) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '>>>'
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- unsigned right shift operator (>>>)
- '>>> operator'
ms.assetid: df48bdfc-8741-46ab-b681-449da57ac95c
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: efb873bedc0a64089c7ec892d6378b4869c0ca21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="unsigned-right-shift-operator-gtgtgt-javascript"></a>符号なし右シフト演算子 (&gt;&gt;&gt;) (JavaScript)
右では、サインインを維持することがなく、式の各ビットをシフトします。  
  
## <a name="syntax"></a>構文  
  
```  
  
result = expression1 >>> expression2  
```  
  
## <a name="parameters"></a>パラメーター  
 *結果*  
 任意の変数。  
  
 *expression1*  
 任意の式。  
  
 *expression2*  
 任意の式。  
  
## <a name="remarks"></a>コメント  
 **>>>** 演算子は、の各ビットをシフト*expression1*で指定されたビット数だけ右*expression2*です。 ゼロは、左からに入力されます。 右側の外に移動桁は破棄されます。 例:  
  
```JavaScript  
var temp  
temp = -14 >>> 2  
```  
  
 変数*temp*初期値-14 (2 の補数バイナリで 11111111 11111111 11111111 11110010) が含まれています。 右に 2 ビットの場合、値は 1073741820 (で 00111111 11111111 11111111 11111100)。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [符号なし右シフト代入演算子 (>>> =)](../../javascript/reference/unsigned-right-shift-assignment-operator-decrement-equal-javascript.md)   
 [ビットごとの左シフト演算子 (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [ビットごとの右シフト演算子 (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)