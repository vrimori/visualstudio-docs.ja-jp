---
title: "String.fromCharCode 関数 (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: fromCharCode
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- fromCharCodeAt method
- characters, from Unicode
ms.assetid: f64120c1-23a7-48ca-8d1c-db3e8856cab4
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dbcd9062d7da0b73647c1d9eb6cc207af23c3532
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="stringfromcharcode-function-javascript"></a>String.fromCharCode 関数 (JavaScript)
1 つ以上の Unicode のコード値から 1 つの文字列を作成します。  
  
## <a name="syntax"></a>構文  
  
```  
String.fromCharCode([code1[, code2[, ...[, codeN]]]])   
```  
  
## <a name="parameters"></a>パラメーター  
 `String`  
 必須です。 `String` オブジェクト。  
  
 `code1`, . 。 。 , `codeN`  
 省略可能です。 一連の文字列に変換する Unicode 文字の値。 引数がない場合、結果、空の文字列です。  
  
## <a name="remarks"></a>コメント  
 この関数を呼び出す、`String`オブジェクト、文字列インスタンスではなく、します。  
  
 次の例では、このメソッドを使用する方法を示します。  
  
```JavaScript  
var test = String.fromCharCode(112, 108, 97, 105, 110);  
document.write(test);  
  
// Output: plain  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [charCodeAt メソッド (String)](../../javascript/reference/charcodeat-method-string-javascript.md)