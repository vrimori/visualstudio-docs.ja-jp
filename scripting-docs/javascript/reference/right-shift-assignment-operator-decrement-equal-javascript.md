---
title: "右シフト代入演算子 (&gt;&gt;=) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: '>>='
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- '>>= operator [JavaScript]'
- right shift operators [JavaScript]
- assignment operators, JavaScript
ms.assetid: 8c1f7f90-e3ac-42ee-94f2-5ccc47d7aef6
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cb93d146ad00bd19c09fb4cfca3af776a11f245d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="right-shift-assignment-operator-gtgt-javascript"></a>右シフト代入演算子 (&gt;&gt;=) (JavaScript)
式の値で指定されたビット数だけ変数の値を右にシフトし、符号は保持して、その結果を変数に代入します。  
  
## <a name="syntax"></a>構文  
  
```  
  
result >>= expression  
```  
  
## <a name="parameters"></a>パラメーター  
 *結果*  
 任意の変数。  
  
 *式*  
 任意の式。  
  
## <a name="remarks"></a>コメント  
 使用して、  **>>=** 演算子まったく同じであるを指定するとします。  
  
```JavaScript  
result = result >> expression  
```  
  
 **>>=** 演算子は、の各ビットをシフト*結果*で指定されたビット数だけ右*式*です。 符号ビットの*結果*左側の桁の数字の塗りつぶしに使用します。 右側の外に移動桁は破棄されます。 たとえば、次のコードが評価された後*temp* -4 の値を持つ: 14 (で 11110010) 右に 2 ビット equals-4 (で 11111100) にシフトします。  
  
```JavaScript  
var temp  
temp = -14  
temp >>= 2  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ビットごとの左シフト演算子 (<\<)](../../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)   
 [ビットごとの右シフト演算子 (>>)](../../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)   
 [符号なし右シフト演算子 (>>>)](../../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)