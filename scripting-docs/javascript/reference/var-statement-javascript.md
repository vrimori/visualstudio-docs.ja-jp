---
title: "var ステートメント (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/22/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: var_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- declaring variables, var statement
- var statement
ms.assetid: 56f900af-a5c4-4667-9664-5956d30f0aae
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839b6904fa59b6f4ea9a5c4d8e00213cd351517a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="var-statement-javascript"></a>var ステートメント (JavaScript)
変数を宣言します。  
  
## <a name="syntax"></a>構文  
  
```  
var variable1 = value1  
```  
  
## <a name="parameters"></a>パラメーター  
 `variable1`  
 宣言される変数の名前を指定します。  
  
 `value1`  
 変数に代入する初期値を指定します。  
  
## <a name="remarks"></a>コメント  
 使用して、`var`変数を宣言するステートメント。 変数には、スクリプトでそれを宣言するとき、または後で値を代入できます。  
  
 変数を宣言すると、最初に、スクリプトに表示されます。  
  
 使用せずに変数を宣言することができます、`var`キーワードとそれに値を割り当てます。 これと呼ばれますが、*暗黙の宣言*、お勧めできません。 暗黙の宣言では、グローバル変数のスコープを示します。 プロシージャ レベルで変数を宣言するときに、通常たくないにグローバル スコープを設定します。 グローバル変数のスコープを提供しないようにを使用する必要があります、`var`変数の宣言でキーワード。  
  
 `var` ステートメントで変数を初期化しない場合は、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 値の `undefined` が自動的に代入されます。  
  
## <a name="example"></a>例  
 次の例では、使用、`var`ステートメントです。  
  
```JavaScript  
var index;  
var name = "Thomas Jefferson";  
var answer = 42, counter, numpages = 10;  
var myarray = new Array();  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [function ステートメント](../../javascript/reference/function-statement-javascript.md)   
 [New 演算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array オブジェクト](../../javascript/reference/array-object-javascript.md)   
 [変数](../../javascript/variables-javascript.md)