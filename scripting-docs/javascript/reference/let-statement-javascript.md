---
title: "let ステートメント (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: let_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- let statement
- declaring variables, let statement
ms.assetid: c7e4f8a9-8f54-47b6-aed2-956959c1ecfd
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c447a1bf0c430771ff146965a592f7e160e2055b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="let-statement-javascript"></a>let ステートメント (JavaScript)
ブロック スコープの変数を宣言します。  
  
## <a name="syntax"></a>構文  
  
```  
let variable1 = value1  
```  
  
#### <a name="parameters"></a>パラメーター  
 `variable1`  
 宣言される変数の名前を指定します。  
  
 `value1`  
 変数に代入する初期値を指定します。  
  
## <a name="remarks"></a>コメント  
 `let` ステートメントを使用して、スコープが宣言されたブロックに制限されている、変数を宣言します。 変数には、スクリプトでそれを宣言するとき、または後で値を代入できます。  
  
 `let` を使用して宣言された変数は、宣言の前に使用するとエラーになります。  
  
 `let` ステートメントで変数を初期化しない場合は、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 値の `undefined` が自動的に代入されます。  
  
## <a name="example"></a>例  
 次の例は、`let` ステートメントの使用方法を示します。  
  
```JavaScript  
var  l = 10;  
{  
    let l = 2;  
   // At this point, l = 2.  
}  
// At this point, l = 10.  
  
// Additional ways to declare a variable using let.  
let index;  
let name = "Thomas Jefferson";  
let answer = 42, counter, numpages = 10;  
let myarray = new Array();  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [const ステートメント](../../javascript/reference/const-statement-javascript.md)   
 [New 演算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array オブジェクト](../../javascript/reference/array-object-javascript.md)   
 [変数](../../javascript/variables-javascript.md)