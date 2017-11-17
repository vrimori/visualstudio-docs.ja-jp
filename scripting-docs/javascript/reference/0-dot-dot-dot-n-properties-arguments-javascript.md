---
title: "0... n プロパティ (arguments) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: 0...n
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: 0...n properties
ms.assetid: 52857c4b-3d56-4500-93ff-4db4729c2578
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f46c7dafef1cdc27d27f619936349637af172740
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="0n-properties-arguments-javascript"></a>0...n プロパティ (arguments) (JavaScript)
個々 の引数からの実際の値を返します、**引数**によって返されるオブジェクト、**引数**実行中の関数のプロパティです。  
  
## <a name="syntax"></a>構文  
  
```  
[function.]arguments[[0|1|2|...|n]]  
```  
  
## <a name="parameters"></a>パラメーター  
 *function*  
 省略可能です。 現在実行中の名前`Function`オブジェクト。  
  
 0、1、2、 *n では、*  
 必須です。 0 の範囲の負でない整数 *n*  0 が 1 番目の引数を表すと *n* の最後の引数を表します。 最後の引数の値 *n* は**arguments.length 1**です。  
  
## <a name="remarks"></a>コメント  
 0 は、返される値。 」を参照してください。 」を参照してください。 n 個のプロパティは、実行中の関数に渡される実際の値です。 実際には引数の配列、中に個々 の引数を構成する、**引数**オブジェクト配列の要素がアクセスされる同じ方法でアクセスされます。  
  
## <a name="example"></a>例  
 次の例では、使用、 **0.**  ***n***プロパティ、**引数**オブジェクト。 例を完全に理解するには、1 つまたは複数の引数を関数に渡します。  
  
```JavaScript  
function ArgTest(){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello", new Date()));  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用先**:[引数オブジェクト](../../javascript/reference/arguments-object-javascript.md)&#124;です。[関数オブジェクト](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [length プロパティ (arguments)](../../javascript/reference/length-property-arguments-javascript.md)   
 [length プロパティ (Function)](../../javascript/reference/length-property-function-javascript.md)