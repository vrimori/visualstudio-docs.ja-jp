---
title: arguments オブジェクト (JavaScript) |Microsoft ドキュメント
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
- arguments
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arguments, arguments object
- arguments object
ms.assetid: 5eb79ca9-bbb8-4a42-aaf5-16a93ecb425f
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a5c526d19ad5469d9d099f51cc5a2e2d089814f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634222"
---
# <a name="arguments-object-javascript"></a>arguments オブジェクト (JavaScript)
現在実行中の関数の引数、およびその呼び出し元の関数を表すオブジェクトです。  
  
## <a name="syntax"></a>構文  
  
```  
[function.]arguments[n]  
```  
  
## <a name="parameters"></a>パラメーター  
 *function*  
 省略可能です。 現在実行中の名前`Function`オブジェクト。  
  
 *n*  
 必須です。 渡される引数の値を 0 から始まるインデックス、`Function`オブジェクト。  
  
## <a name="remarks"></a>コメント  
 明示的に作成することはできません、**引数**オブジェクト。 **引数**オブジェクトのみが有効になり、関数の実行を開始します。 **引数**関数のオブジェクトは、配列ではありませんが、個々 の引数は配列要素は、同じ方法でアクセスします。 インデックス *n* のいずれかへの参照を実際には、 **0**  ***n*** のプロパティ、**引数**オブジェクト。  
  
## <a name="example"></a>例  
 次の例では、使用、**引数**オブジェクト。  
  
```JavaScript  
function ArgTest(a, b)  
{  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
   s += "<br />";  
  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++)  
   {  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
  
   document.write(s);  
}  
  
ArgTest(1, 2, "hello", new Date())  
  
// Output:  
// Expected Arguments: 2  
// Passed Arguments: 4  
// The individual arguments are: 1 2 hello Tues Jan 8 08:27:09 PST 20xx  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [0... n プロパティ (arguments)](../../javascript/reference/0-dot-dot-dot-n-properties-arguments-javascript.md)   
 [callee プロパティ (arguments)](../../javascript/reference/callee-property-arguments-javascript.md)   
 [length プロパティ (arguments)](../../javascript/reference/length-property-arguments-javascript.md)