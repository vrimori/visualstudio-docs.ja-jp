---
title: "arguments プロパティ (Function) (JavaScript) |Microsoft ドキュメント"
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
- arguments
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arguments, arguments property
- Arguments property
ms.assetid: efc7a1ee-0880-4f05-b0f2-808f31a4af1d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b0b18fb8164639119e5db5e7a5d76b4280f9c9d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="arguments-property-function-javascript"></a>arguments プロパティ (Function) (JavaScript)
現在実行中の引数を取得`Function`オブジェクト。  
  
## <a name="syntax"></a>構文  
  
```  
  
function.arguments  
```  
  
## <a name="remarks"></a>コメント  
 `function`引数を現在実行中の関数の名前は省略できます。  
  
 このプロパティは、可変個の引数を処理する関数を使用します。 **長さ**のプロパティ、`arguments`オブジェクトには、関数に渡された引数の数が含まれています。 含まれている個々 の引数、`arguments`オブジェクトは、配列要素のアクセスは、同じ方法でアクセスできます。  
  
## <a name="example"></a>例  
 `arguments` プロパティの使用例を次に示します。  
  
```JavaScript  
function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
//Output: function ArgTest(arg1, arg2){  
   var s = "";  
   s += "The individual arguments are: "  
   for (n = 0; n < arguments.length; n++){  
      s += ArgTest.arguments[n];  
      s += " ";  
   }  
   return(s);  
}  
document.write(ArgTest(1, 2, "hello"));  
  
// Output: The individual arguments are: 1 2 hello  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [arguments オブジェクト](../../javascript/reference/arguments-object-javascript.md)   
 [function ステートメント](../../javascript/reference/function-statement-javascript.md)