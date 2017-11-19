---
title: "toFixed メソッド (Number) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: toFixed
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: toFixed method
ms.assetid: b5f03400-865e-4ab2-818c-f734c0f6d6f0
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd51dd67632f4e6417fee72fd19575025423bbf1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="tofixed-method-number-javascript"></a>toFixed メソッド (Number) (JavaScript)
固定小数点表記の数値を表します。  
  
## <a name="syntax"></a>構文  
  
```  
  
numObj.toFixed([fractionDigits])  
```  
  
## <a name="parameters"></a>パラメーター  
 `numObj`  
 必要な A`Number`オブジェクト。  
  
 `fractionDigits`  
 省略可能です。 小数点後の数字の数。 0 ~ 20 の範囲でなければなりません。  
  
## <a name="return-value"></a>戻り値  
 固定小数点表記法で数値の文字列形式を返しますを含む`fractionDigits`小数点後の数字です。  
  
 場合`fractionDigits`が指定されていないか、**未定義**既定値は 0 です。  
  
## <a name="example"></a>例  
 `toFixed` の使用例を次のコードに示します。  
  
```JavaScript  
var num = new Number(123);  
var fix = num.toFixed();  
document.write(fix);  
document.write("<br/>");  
  
num = new Number(123.456);  
fix = num.toFixed(5);  
document.write(fix);  
  
// Output:  
// 123  
123.45600  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用されます**:[オブジェクトの数](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [toExponential メソッド (Number)](../../javascript/reference/toexponential-method-number-javascript.md)   
 [toPrecision メソッド (Number)](../../javascript/reference/toprecision-method-number-javascript.md)