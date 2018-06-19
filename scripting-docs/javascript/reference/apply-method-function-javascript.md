---
title: apply メソッド (Function) (JavaScript) |Microsoft ドキュメント
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
- apply
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Apply method
ms.assetid: b36df78e-b14b-46ca-b5cb-de752d80f40a
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5a06a37006937b07214bf5a314d5151c3b658acf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24633362"
---
# <a name="apply-method-function-javascript"></a>apply メソッド (Function) (JavaScript)
関数の代わりに、指定したオブジェクトを呼び出し、`this`関数、および関数の引数の指定された配列の値。  
  
## <a name="syntax"></a>構文  
  
```  
apply([thisObj[,argArray]])  
```  
  
## <a name="parameters"></a>パラメーター  
 `thisObj`  
 省略可能です。 として使用するオブジェクト、`this`オブジェクト。  
  
 `argArray`  
 省略可能です。 一連の関数に渡される引数。  
  
## <a name="remarks"></a>コメント  
 場合`argArray`「オブジェクトが必要です」エラーが発生し、有効なオブジェクトではありません。  
  
 どちらの場合`argArray`も`thisObj`が提供されたオリジナル`this`としてオブジェクトを使用して`thisObj`引数が渡されないとします。  
  
## <a name="example"></a>例  
 次のコードでは、適用方法を使用する方法を示します。  
  
```JavaScript  
function callMe(arg1, arg2){  
    var s = "";  
  
    s += "this value: " + this;  
    s += "<br />";  
    for (i in callMe.arguments) {  
        s += "arguments: " + callMe.arguments[i];  
        s += "<br />";  
    }  
    return s;  
}  
  
document.write("Original function: <br/>");  
document.write(callMe(1, 2));  
document.write("<br/>");  
  
document.write("Function called with apply: <br/>");  
document.write(callMe.apply(3, [ 4, 5 ]));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with apply:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Function オブジェクト](../../javascript/reference/function-object-javascript.md)