---
title: "const ステートメント (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: const_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- declaring variables, const statement
- const statement
ms.assetid: 3ad0840f-437f-4163-9571-86ecc5ddb987
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68130cec4f1b1fe89d2fe3e673b28963d79aebde
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="const-statement-javascript"></a>const ステートメント (JavaScript)
定数値を含むブロック スコープの変数を宣言します。  
  
## <a name="syntax"></a>構文  
  
```  
const constant1 = value1  
```  
  
#### <a name="parameters"></a>パラメーター  
 `constant1`  
 宣言される変数の名前を指定します。  
  
 `value1`  
 変数に代入する初期値を指定します。  
  
## <a name="remarks"></a>コメント  
 `const` ステートメントを使用して、スコープが宣言されたブロックに制限されている、定数値を含む変数を宣言します。 この変数の値は変更できません。  
  
 `const` を使用して宣言された変数は、宣言時に初期化される必要があります。  
  
## <a name="example"></a>例  
 次の例は、`const` ステートメントの使用方法を示します。  
  
```JavaScript  
var c = 10;  
{  
    const c = 2;  
   // At this point, c = 2.  
}  
// At this point, c = 10.  
  
// Additional ways to declare a variable using const.  
const name = "Thomas Jefferson";  
const answer = 42, numpages = 10;  
const myarray = new Array();  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [let ステートメント](../../javascript/reference/let-statement-javascript.md)   
 [New 演算子](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Array オブジェクト](../../javascript/reference/array-object-javascript.md)   
 [変数](../../javascript/variables-javascript.md)