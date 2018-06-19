---
title: length プロパティ (arguments) (JavaScript) |Microsoft ドキュメント
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
- length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- length property (arguments)
- Length property
ms.assetid: 3cf36823-15bc-489b-a951-24c4923d9dba
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cede75a91244442f5f28ec9f71b7128814bed5d2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637912"
---
# <a name="length-property-arguments-javascript"></a>length プロパティ (arguments) (JavaScript)
関数を呼び出すときに実際に渡された引数の数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
[function.]arguments.length  
```  
  
## <a name="remarks"></a>コメント  
 省略可能な*関数*引数は、現在実行中の名前`Function`オブジェクト。  
  
 **長さ**のプロパティ、**引数**オブジェクトが実際に渡される引数の数、スクリプト エンジンによって初期化されて、`Function`オブジェクトその関数の実行が開始されるときです。  
  
## <a name="example"></a>例  
 次の例では、使用、**長さ**のプロパティ、**引数**オブジェクト。 例を完全に理解するには、2 つの引数が予想よりも関数に引数の数を渡します。  
  
```JavaScript  
function ArgTest(a, b){  
   var s = "";  
  
   s += "Expected Arguments: " + ArgTest.length;  
   s += "<br />";  
   s += "Passed Arguments: " + arguments.length;  
  
   document.write (s);  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **適用先**:[引数オブジェクト](../../javascript/reference/arguments-object-javascript.md)&#124;です。[関数オブジェクト](../../javascript/reference/function-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [arguments プロパティ (Function)](../../javascript/reference/arguments-property-function-javascript.md)   
 [length プロパティ (Array)](../../javascript/reference/length-property-array-javascript.md)   
 [length プロパティ (String)](../../javascript/reference/length-property-string-javascript.md)