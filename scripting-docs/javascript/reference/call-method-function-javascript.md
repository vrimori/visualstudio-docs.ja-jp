---
title: call メソッド (Function) (JavaScript) |Microsoft ドキュメント
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
- call
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- call method
ms.assetid: fa356dec-48e6-4f75-8bf3-c1814a76818f
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ef871f85459ad875a747ae79c7c054b30a82e55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634112"
---
# <a name="call-method-function-javascript"></a>call メソッド (Function) (JavaScript)
現在のオブジェクトの代わりに、他のオブジェクトを使用してメソッドを呼び出します。  
  
## <a name="syntax"></a>構文  
  
```  
call([thisObj[, arg1[, arg2[,  [, argN]]]]])  
```  
  
## <a name="parameters"></a>パラメーター  
 `thisObj`  
 省略可能です。 現在のオブジェクトとして使用するオブジェクトを指定します。  
  
 `arg1, arg2, , argN`  
 省略可能です。 メソッドに渡す引数のリストです。  
  
## <a name="remarks"></a>コメント  
 別のオブジェクトに代わってメソッドを呼び出すときに `call` メソッドを使用します。 このメソッドを使用すると、関数の `this` オブジェクトを元のコンテキストから `thisObj` で指定した新しいオブジェクトに変更できます。  
  
 `thisObj` を指定しない場合は、`global` オブジェクトが `thisObj` として使用されます。  
  
## <a name="example"></a>例  
 `call` メソッドの使用例を次のコードに示します。  
  
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
  
document.write("Function called with call: <br/>");  
document.write(callMe.call(3, 4, 5));  
  
// Output:   
// Original function:   
// this value: [object Window]  
// arguments: 1  
// arguments: 2  
  
// Function called with call:   
// this value: 3  
// arguments: 4  
// arguments: 5  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Function オブジェクト](../../javascript/reference/function-object-javascript.md)   
 [apply メソッド (Function)](../../javascript/reference/apply-method-function-javascript.md)