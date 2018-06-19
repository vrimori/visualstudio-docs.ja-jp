---
title: 関数のステートメント (JavaScript) |Microsoft ドキュメント
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
- function_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- new operator
- declaring functions, syntax
- function statement
- declaring functions
ms.assetid: cc9cfd43-1305-41c8-ad67-545d20f4fafe
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e5fac3647e9374a9c909a420b73b86354cac69b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636872"
---
# <a name="function-statement-javascript"></a>function ステートメント (JavaScript)
新しい関数を宣言します。  
  
## <a name="syntax"></a>構文  
  
```  
function functionname ([arg1 [, arg2 [,...[, argN]]]]) {  
    statements  
}   
```  
  
## <a name="parameters"></a>パラメーター  
 `functionname`  
 必須です。 関数の名前。  
  
 `arg1...argN`  
 省略可能です。 省略可能な、関数が認識できる引数のコンマ区切りのリスト。  
  
 `statements`  
 省略可能です。 1 つまたは複数[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]ステートメントです。  
  
## <a name="remarks"></a>コメント  
 使用して、`function`を後で使用するための関数を宣言するステートメント。 含まれているコード`statements`関数が呼び出されるまでから別の場所で、スクリプトでは実行されません。  
  
 [返す](../../javascript/reference/return-statement-javascript.md)関数から値を返すステートメントを使用します。 使用する必要はありません、`return`ステートメント以外のプログラムは、関数の末尾に達したときに戻ります。 ない場合は`return`ステートメントが関数で実行される場合、または、`return`ステートメントが式を持たず、値を返します`undefined`です。  
  
> [!NOTE]
>  関数を呼び出すときに、かっこで囲むと、必要な引数を含めることを確認します。 かっこのない関数を呼び出すには、関数、関数の結果ではないへの参照が返されます。  
  
## <a name="example"></a>例  
 次の例は、`function` ステートメントの使用方法を示します。  
  
```JavaScript  
function myfunction (arg1, arg2) {  
    var r = arg1 * arg2;  
    return(r);  
}  
```  
  
## <a name="example"></a>例  
 関数は、変数に代入できます。 このことを次の例で説明します。  
  
```JavaScript  
function AddFive(x) {  
    return x + 5;  
}  
  
function AddTen(x) {  
    return x + 10;  
}  
  
var condition = false;  
  
var MyFunc;  
if (condition) {  
    MyFunc = AddFive;  
}  
else {  
    MyFunc = AddTen;  
}  
  
var result = MyFunc(123);  
// Output: 133  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [new 演算子](../../javascript/reference/new-operator-decrementjavascript.md)