---
title: toPrecision メソッド (Number) (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- toPrecision
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- toPrecision method
ms.assetid: ac13c82f-1038-447a-823f-f755bba535ca
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeab7642dcd88677d1b5a7102e3cf342d7ee1d29
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640722"
---
# <a name="toprecision-method-number-javascript"></a>toPrecision メソッド (Number) (JavaScript)
指定された数の数字の指数または固定小数点表記のいずれかの数値を表します。  
  
## <a name="syntax"></a>構文  
  
```  
  
numObj.toPrecision([precision])  
```  
  
## <a name="parameters"></a>パラメーター  
 `numObj`  
 必須です。 `Number` オブジェクト。  
  
 `precision`  
 省略可能です。 有効桁数の数。 1-21 の範囲でなければなりません。  
  
## <a name="return-value"></a>戻り値  
 指数表記法で数値の`precision`- 1 桁の数字が小数点の後に返されます。 固定小数点表記での数値の`precision`有効桁数が返されます。  
  
 場合`precision`が指定されていないか、**未定義**、 **toString**代わりにメソッドが呼び出されます。  
  
## <a name="example"></a>例  
 `toPrecision` の使用例を次のコードに示します。  
  
```JavaScript  
var num = new Number(123);  
var prec = num.toPrecision();  
document.write(prec);  
document.write("<br/>");  
  
num = new Number(123.456);  
prec = num.toPrecision(5);  
document.write(prec);  
  
// Output:  
// 123  
// 123.46  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用されます**:[オブジェクトの数](../../javascript/reference/number-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [toFixed メソッド (Number)](../../javascript/reference/tofixed-method-number-javascript.md)   
 [toExponential メソッド (Number)](../../javascript/reference/toexponential-method-number-javascript.md)