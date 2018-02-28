---
title: "演算子 (JavaScript) | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- JavaScript, operators
ms.assetid: b8602b69-aba9-46e8-86e1-cb533ad41410
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9d0a098418399dba19b77a12c057a3fba334e31
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="operators-javascript"></a>演算子 (JavaScript)
[!INCLUDE[javascript](../javascript/includes/javascript-md.md)] には、算術演算子、論理演算子、ビット処理演算子、代入演算子、およびその他のさまざまな演算子があります。 説明と例については、特定の演算子のトピックをご覧ください。  
  
## <a name="computational-operators"></a>算術演算子  
  
|説明|シンボル|  
|-----------------|------------|  
|[単項マイナス符号](../javascript/reference/subtraction-operator-decrement-javascript.md)|-|  
|[インクリメント](../javascript/reference/increment-and-decrement-operators-javascript.md)|++|  
|[デクリメント](../javascript/reference/increment-and-decrement-operators-javascript.md)|--|  
|[乗算](../javascript/reference/multiplication-operator-decrement-javascript.md)|*|  
|[除算](../javascript/reference/division-operator-decrement-javascript.md)|/|  
|[剰余](../javascript/reference/modulus-operator-decrementjavascript.md)|%|  
|[加算](../javascript/reference/addition-operator-decrement-javascript.md)|+|  
|[減算](../javascript/reference/subtraction-operator-decrement-javascript.md)|-|  
  
## <a name="logical-operators"></a>論理演算子  
  
|説明|シンボル|  
|-----------------|------------|  
|[論理 NOT](../javascript/reference/logical-not-operator-decrement-exclpt-javascript.md)|!|  
|[より小さい](../javascript/reference/comparison-operators-javascript.md)|\<|  
|[より大きい](../javascript/reference/comparison-operators-javascript.md)|>|  
|[以下](../javascript/reference/comparison-operators-javascript.md)|\<=|  
|[以上](../javascript/reference/comparison-operators-javascript.md)|>=|  
|[等価](../javascript/reference/comparison-operators-javascript.md)|==|  
|[非等価](../javascript/reference/comparison-operators-javascript.md)|!=|  
|[論理 AND](../javascript/reference/logical-and-operator-decrement-javascript.md)|&&|  
|[論理 OR](../javascript/reference/logical-or-operator-decrement-javascript.md)|&#124;&#124;|  
|[条件 (三項)](../javascript/reference/conditional-ternary-operator-decrement-javascript.md)|?:|  
|[コンマ](../javascript/reference/comma-operator-decrement-javascript.md)|,|  
|[厳密等価](../javascript/reference/comparison-operators-javascript.md)|===|  
|[厳密非等価](../javascript/reference/comparison-operators-javascript.md)|!==|  
  
## <a name="bitwise-operators"></a>ビット処理演算子  
  
|説明|シンボル|  
|-----------------|------------|  
|[ビットごとの NOT](../javascript/reference/bitwise-not-operator-decrement-tilde-javascript.md)|~|  
|[ビットごとの左シフト](../javascript/reference/bitwise-left-shift-operator-decrement-javascript.md)|<\<|  
|[ビットごとの右シフト](../javascript/reference/bitwise-right-shift-operator-decrement-javascript.md)|>>|  
|[符号なしの右シフト](../javascript/reference/unsigned-right-shift-operator-decrement-javascript.md)|>>>|  
|[ビットごとの AND](../javascript/reference/bitwise-and-operator-decrement-javascript.md)|&|  
|[ビットごとの XOR](../javascript/reference/bitwise-xor-operator-decrement-hat-javascript.md)|^|  
|[ビットごとの OR](../javascript/reference/bitwise-or-operator-decrement-javascript.md)|&#124;|  
  
## <a name="assignment-operators"></a>代入演算子  
  
|説明|シンボル|  
|-----------------|------------|  
|[代入](../javascript/reference/assignment-operator-decrement-equal-javascript.md)|=|  
|[複合代入](../javascript/reference/compound-assignment-operators-javascript.md)|*OP*= (+=、&= など)|  
  
## <a name="miscellaneous-operators"></a>その他の演算子  
  
|説明|シンボル|  
|-----------------|------------|  
|[delete](../javascript/reference/delete-operator-decrementjavascript.md)|delete|  
|[typeof](../javascript/reference/typeof-operator-decrementjavascript.md)|typeof|  
|[void](../javascript/reference/void-operator-decrementjavascript.md)|void|  
|[instanceof](../javascript/reference/instanceof-operator-decrementjavascript.md)|instanceof|  
|[new](../javascript/reference/new-operator-decrementjavascript.md)|new|  
|[in](../javascript/reference/in-operator-decrementjavascript.md)|in|  
  
## <a name="equality-and-strict-equality"></a>等価演算子と厳密等価演算子  
 == (等価) と === (厳密等価) の違いは、等価演算子が等価をチェックする前に異なる型の値の型変換を強制的に実行することです。 たとえば、文字列 "1" と数値 1 を比較すると true として比較されます。 一方、厳密等価演算子は、異なる型の型変換を強制的に実行しないので、文字列 "1" と数値 1 は等価になりません。  
  
 プリミティブな文字列、数値、およびブール値は値によって比較されます。 同じ値を持つ場合は等価と見なされます。 オブジェクト (`Array`、`Function`、`String`、**Number**、`Boolean`、**Error**、`Date`、`RegExp` オブジェクト) は、参照渡しで比較されます。 これらの型の 2 つの変数の値が同じであっても、厳密に同じオブジェクトを参照している場合だけ等価になります。  
  
 例:  
  
```JavaScript  
// Two strings with the same value.  
var string1 = "Hello";  
var string2 = "Hello";  
  
// Two String objects with the same value.  
var StringObject1 = new String(string1);  
var StringObject2 = new String(string2);  
  
if (string1 == string2)  
    document.write("string1 is equal to string2 <br/>");  
  
if (StringObject1 != StringObject2)  
    document.write("StringObject1 is not equal to StringObject2 <br/>");  
  
// To compare the values of String objects, use the toString() or valueOf() methods.  
if (StringObject1.valueOf() == StringObject2.valueOf())  
    document.write("The value of StringObject1 is equal to the value of StringObject2");  
  
//Output:  
// string1 is equal to string2   
// StringObject1 is not equal to StringObject2   
// The value of StringObject1 is equal to the value of StringObject2  
  
```