---
title: "toExponential メソッド (Number) (JavaScript) |Microsoft ドキュメント"
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
- toExponential
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toExponential method
ms.assetid: 7c4a6d84-3c1f-4cc4-a67d-7753e5d4ed66
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fff2f2bc0c443fa9308c8d01dcea42a3cec9ff04
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="toexponential-method-number-javascript"></a>toExponential メソッド (Number) (JavaScript)
指数表記の数値を表します。  
  
## <a name="syntax"></a>構文  
  
```  
  
numObj. toExponential([fractionDigits])  
```  
  
## <a name="parameters"></a>パラメーター  
 `numObj`  
 必須です。 A**数**オブジェクト。  
  
 `fractionDigits`  
 省略可能です。 小数点後の数字の数。 0 ~ 20 の範囲でなければなりません。  
  
## <a name="return-value"></a>戻り値  
 指数表記の数値の文字列表現を返します。 文字列、小数点の前に 1 桁の数字を含み、含めることができます`fractionDigits`後の桁数。  
  
 場合`fractionDigits`が指定されていない、`toExponential`メソッドが数を一意に指定するために必要な多くの桁数を返します。  
  
## <a name="example"></a>例  
  
```JavaScript  
var num = new Number(123);  
var exp = num.toExponential();  
document.write(exp);  
document.write("<br/>");  
  
num = new Number(123.456);  
exp = num.toExponential(5);  
document.write(exp);  
  
// Output:   
// 1.23e+2  
// 1.23456e+2  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用されます**:[オブジェクトの数](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [toFixed メソッド (Number)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toPrecision メソッド (Number)](../../javascript/reference/toprecision-method-number-javascript.md)