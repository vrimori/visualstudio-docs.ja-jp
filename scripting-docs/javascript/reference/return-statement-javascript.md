---
title: "return ステートメント (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: return_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- terminating execution
- return statement
- function statement
- return statement, syntax
- return statement, exiting functions in script
ms.assetid: a9130d90-11fb-43f5-a819-7e5435f74c05
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c28f17bed2dfff021ea1aea268bb7a2eb3f3e58
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="return-statement-javascript"></a>return ステートメント (JavaScript)
現在の関数の実行を終了し、戻り値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
return[(][expression][)];   
```  
  
## <a name="remarks"></a>コメント  
 省略可能な*式*引数が関数から返される値。 省略した場合、関数は戻り値を返しません。  
  
 使用する、`return`関数の実行を停止し、値を返すステートメント*式*です。 場合*式*を省略すると、またはまったく`return`ステートメントは、関数内から実行が、現在の関数を呼び出した式には、未定義の値が割り当てられます。  
  
## <a name="example"></a>例  
 次の例は、`return` ステートメントの使用方法を示します。  
  
```JavaScript  
function myfunction(arg1, arg2){  
   var r;  
   r = arg1 * arg2;  
   return(r);  
}  
```  
  
## <a name="example"></a>例  
 次の例は、`return` ステートメントを使用して関数を戻す方法を示します。  
  
```JavaScript  
function doWork() {  
    return function calculate(y) { return y + 1; };  
}  
  
var func = doWork();  
var x = func(5);  
document.write(x);  
  
// Output: 6  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [function ステートメント](../../javascript/reference/function-statement-javascript.md)