---
title: "Number オブジェクト (JavaScript) |Microsoft ドキュメント"
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
- Number_JavaScript
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Number object
ms.assetid: 76e87c37-cf6c-46cc-bafa-04be1fe3d78d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7cbe58fdc9673a8fffe35b8b15d7edbf86ffa655
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="number-object-javascript"></a>Number オブジェクト (JavaScript)
任意の種類の数値を表すオブジェクト。 JavaScript のすべての数値は、64 ビットの浮動小数点数です。  
  
## <a name="syntax"></a>構文  
  
```  
  
numObj = new Number(value)  
```  
  
## <a name="parameters"></a>パラメーター  
 `numObj`  
 必須です。 `Number` オブジェクトを代入する変数名を指定します。  
  
 `value`  
 必須です。 数値。  
  
## <a name="remarks"></a>コメント  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] は、変数が数値に設定されている場合 (`Number` など)、`var num = 255.336;` オブジェクトを作成します。 `Number` オブジェクトの明示的な作成が必要になることはほとんどありません。  
  
 `Number` オブジェクトは、`Object` オブジェクトから継承したプロパティとメソッドに加えて、それぞれ独自のプロパティとメソッドを持ちます。 数値が追加されたり文字列と連結されたりする場合などの特定の状況下、または `toString` メソッドを使用した場合には、数値は文字列に変換されます。 詳細については、次を参照してください。[加算演算子 (+)](../../javascript/reference/addition-operator-decrement-javascript.md)です。  
  
 JavaScript には複数の number 定数があります。 完全な一覧についてを参照してください。 [Number 定数](../../javascript/reference/number-constants-javascript.md)です。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="properties"></a>プロパティ  
 `Number` オブジェクトのプロパティを次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|[constructor プロパティ](../../javascript/reference/constructor-property-object-javascript.md)|オブジェクトを作成する関数を指定します。|  
|[prototype プロパティ](../../javascript/reference/prototype-property-object-javascript.md)|指定されたオブジェクトのクラスのプロトタイプへの参照を返します。|  
  
## <a name="functions"></a>関数  
 次の表の機能、`Number`オブジェクト。  
  
|関数|説明|  
|--------------|-----------------|  
|[Number.isFinite 関数](../../javascript/reference/number-isfinite-function-number-javascript.md)|値が有限であるかどうかを示すブール値を返します。|  
|[Number.isInteger 関数](../../javascript/reference/number-isinteger-function-number-javascript.md)|値が整数であるかどうかを示すブール値を返します。|  
|[Number.isNaN 関数](../../javascript/reference/number-isnan-function-number-javascript.md)|値が予約済みの値 `NaN` (非数) であるかどうかを示すブール値を返します。|  
|[Number.isSafeInteger](../../javascript/reference/number-issafeinteger-number-javascript.md)|JavaScript で値を安全に表現できるかどうかを示すブール値を返します。|  
  
## <a name="methods"></a>メソッド  
 次の表のメソッド、`Number`オブジェクト。  
  
|メソッド|説明|  
|------------|-----------------|  
|[hasOwnProperty メソッド](../../javascript/reference/hasownproperty-method-object-javascript.md)|指定した名前のプロパティがオブジェクトにあるかどうかを表すブール値を返します。|  
|[isPrototypeOf メソッド](../../javascript/reference/isprototypeof-method-object-javascript.md)|オブジェクトが、別のオブジェクトのプロトタイプ階層に存在するかどうかを表すブール値を返します。|  
|[propertyIsEnumerable メソッド](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|指定したプロパティがオブジェクトの一部であるかどうか、および列挙可能かどうかを表すブール値を返します。|  
|[toExponential メソッド](../../javascript/reference/toexponential-method-number-javascript.md)|数値を指数表記の文字列として返します。|  
|[toFixed メソッド](../../javascript/reference/tofixed-method-number-javascript.md)|数値を固定小数点表記の文字列として返します。|  
|[toLocaleString メソッド](../../javascript/reference/tolocalestring-number.md)|現在のロケールに基づいて、オブジェクトを文字列に変換して返します。|  
|[toPrecision メソッド](../../javascript/reference/toprecision-method-number-javascript.md)|指定された桁数の指数表記または固定小数点表記の数値を文字列として返します。|  
|[toString メソッド](../../javascript/reference/tostring-method-object-javascript.md)|オブジェクトの値を表す文字列を返します。|  
|[valueOf メソッド](../../javascript/reference/valueof-method-object-javascript.md)|指定されたオブジェクトのプリミティブ値を返します。|  
  
## <a name="see-also"></a>関連項目  
 [JavaScript オブジェクト](../../javascript/reference/javascript-objects.md)   
 [Math オブジェクト](../../javascript/reference/math-object-javascript.md)   
 [new 演算子](../../javascript/reference/new-operator-decrementjavascript.md)