---
title: "typeof 演算子 (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- typeof_JavaScriptKeyword
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- typeof operator
ms.assetid: ee8a1036-119f-486f-b034-b07bdba87f0c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c79c69e6c447b14e61fa67ccb8600d5d83bebd2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="typeof-operator-javascript"></a>typeof 演算子 (JavaScript)
式のデータ型を識別する文字列を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
typeof[(]expression[)] ;  
```  
  
## <a name="remarks"></a>コメント  
 *式*引数が任意の式がどの型情報を取得します。  
  
 `typeof` 演算子は、型情報を文字列で返します。 `typeof` 演算子が返す文字列は、"number"、"string"、"boolean"、"object"、"function"、"undefined" の 6 つです。  
  
 `typeof` の構文のかっこは省略できます。  
  
## <a name="example"></a>例  
 変数のデータ型を調べる例を次に示します。  
  
```JavaScript  
var index = 5;  
var result = (typeof index === 'number');  
// Output: true  
  
var description = "abc";  
var result = (typeof description === 'string');  
// Output: true  
```  
  
## <a name="example"></a>例  
 宣言されている変数と宣言されていない変数のデータ型が `undefined` かどうかを調べる例を次に示します。  
  
```JavaScript  
var declared;  
var result = (declared === undefined);  
// Output: true  
  
var result = (typeof declared === 'undefined');  
// Output: true  
  
var result = (typeof notDeclared === 'undefined')  
// Output: true  
  
var obj = {};  
var result = (typeof obj.propNotDeclared === 'undefined');  
// Output: true  
  
// An undeclared variable cannot be used in a comparison without  
// the typeof operator, so the next line generates an error.  
//  var result = (notDeclared === undefined);  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Array.isArray 関数](../../javascript/reference/array-isarray-function-javascript.md)   
 [Object.getPrototypeOf 関数](../../javascript/reference/object-getprototypeof-function-javascript.md)   
 [定数 undefined](../../javascript/reference/undefined-constant-javascript.md)   
 [比較演算子](../../javascript/reference/comparison-operators-javascript.md)   
 [データ型](../../javascript/data-types-javascript.md)   
 [演算子の優先順位](../../javascript/operator-subtractprecedence-javascript.md)   
 [演算子の一覧 (JavaScript)](../../javascript/misc/operator-subtractsummary-javascript.md)