---
title: "instanceof 演算子 (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: instanceof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: instanceOf operator
ms.assetid: 92467bdc-56b5-42dc-adbd-a219776454d2
caps.latest.revision: "17"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 672047cb066a812d16edc693638c3d6d8295798b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="instanceof-operator-javascript"></a>instanceof 演算子 (JavaScript)
オブジェクトが特定のクラスのインスタンスかどうかを示すブール値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
result = object instanceof class  
```  
  
## <a name="parameters"></a>パラメーター  
 `result`  
 必須です。 任意の変数。  
  
 `object`  
 必須です。 任意のオブジェクト式を指定します。  
  
 `class`  
 必須です。 任意の定義済みオブジェクト クラス。  
  
## <a name="remarks"></a>コメント  
 `instanceof` 演算子は、`true` が `object` のインスタンスである場合に `class` を返します。 返します`true`場合`true`場合`class`がオブジェクトのプロトタイプ チェーンに存在します。 `false` が `object` のインスタンスではない場合、または `class` が `object` の場合は `null` を返します。  
  
## <a name="example"></a>例  
 `instanceof` 演算子を使用する方法の例を次に示します。  
  
```JavaScript  
function objTest(obj){  
    var i, t, s = "";  
    t = new Array();  
    t["Date"] = Date;  
    t["Object"] = Object;  
    t["Array"] = Array;  
        for (i in t){  
            if (obj instanceof t[i]) {   
                s += "obj is an instance of " + i + "<br/>";  
            }  
            else {  
                s += "obj is not an instance of " + i + "<br/>";  
        }  
    }  
    return(s);  
}  
  
var obj = new Date();  
document.write(objTest(obj));  
  
// Output:   
// obj is an instance of Date  
// obj is an instance of Object  
// obj is not an instance of Array  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)