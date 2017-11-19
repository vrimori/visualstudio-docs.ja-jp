---
title: "関数オブジェクト (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: function
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Function object
ms.assetid: d3834767-203c-475e-848c-95c423ba15b6
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4392fd57967e6312c96af50bdff2415d0f2dcd4d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="function-object-javascript"></a>Function オブジェクト (JavaScript)
新しい関数を作成します。  
  
## <a name="syntax"></a>構文  
  
```  
function functionName([argname1  [, ...[, argnameN]]])  
{  
   body  
}  
```  
  
## <a name="syntax"></a>構文  
  
```  
  
functionName = new Function( [argname1,  [... argnameN,]] body );  
```  
  
## <a name="parameters"></a>パラメーター  
 `functionName`  
 必須です。 新しく作成された関数の名前  
  
 `argname1...argnameN`  
 省略可能です。 関数が受け取る引数のリスト。  
  
 `body`  
 省略可能です。 ブロックを表す文字列[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]関数が呼び出されたときに実行されるコード。  
  
## <a name="remarks"></a>コメント  
 内の基本的なデータ型は、関数は[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]します。 構文 1 の作成、関数値[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]に変換、`Function`オブジェクトに必要なとき。 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]変換`Function`関数が呼び出された時点では、関数の値に、構文 2 によって作成されたオブジェクト。  
  
 構文 1、標準の新しい関数を作成する方法は、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]です。 構文 2 は、別の形式の関数オブジェクトを明示的に作成するために使用します。  
  
 たとえば、渡された 2 つの引数を追加する関数を宣言するに行うことができます 2 つの方法のいずれかで。  
  
## <a name="example-1"></a>例 1  
  
```JavaScript  
function add(x, y)  
{  
   return(x + y);  
}  
```  
  
## <a name="example-2"></a>例 2  
  
```  
var add = function(x, y) {  
     return(x+y);  
}  
```  
  
 どちらの場合は、次のような行のコードで関数が呼び出します。  
  
```JavaScript  
add(2, 3);  
```  
  
> [!NOTE]
>  関数を呼び出すときに、かっこで囲むと、必要な引数は、常にことを確認します。 かっこのない関数を呼び出すと、関数、関数の戻り値の代わりに、返される自体とします。  
  
## <a name="properties"></a>プロパティ  
 [0... n プロパティ](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)&#124;[arguments プロパティ](../../javascript/reference/arguments-property-function-javascript.md)&#124;です。[callee プロパティ](../../javascript/reference/callee-property-arguments-javascript.md)&#124;です。[caller プロパティ](../../javascript/reference/caller-property-function-javascript.md)&#124;です。[コンス トラクター プロパティ](../../javascript/reference/constructor-property-object-javascript.md)&#124;です。[length プロパティ (Function)](../../javascript/reference/length-property-function-javascript.md) &#124;です。[prototype プロパティ](../../javascript/reference/prototype-property-object-javascript.md)  
  
## <a name="methods"></a>メソッド  
 [apply メソッド](../../javascript/reference/apply-method-function-javascript.md)&#124;です。[bind メソッド](../../javascript/reference/bind-method-function-javascript.md)&#124;です。[メソッドを呼び出す](../../javascript/reference/call-method-function-javascript.md)&#124;です。[toString メソッド](../../javascript/reference/tostring-method-object-javascript.md)&#124;です。[valueOf メソッド](../../javascript/reference/valueof-method-object-javascript.md)  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [function ステートメント](../../javascript/reference/function-statement-javascript.md)   
 [New 演算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [var ステートメント](../../javascript/reference/var-statement-javascript.md)