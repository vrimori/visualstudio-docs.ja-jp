---
title: "length プロパティ (Function) (JavaScript) |Microsoft ドキュメント"
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
- length Property
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Length property
- length property (function)
ms.assetid: fdc8e1c9-0dac-4e1b-ba3a-11073c37ef63
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fbd0334c18da2c6ef8de8366555d79f791e6855
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="length-property-function-javascript"></a>length プロパティ (Function) (JavaScript)
関数に対して定義されている引数の数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
functionName.length  
```  
  
## <a name="remarks"></a>コメント  
 必要な*functionName*関数の名前を指定します。  
  
 **長さ**関数のインスタンスが作成されるときは、関数のプロパティを関数の定義の引数の数、スクリプト エンジンによって初期化します。  
  
 引数の値と異なるさまざまな関数が呼び出されたときに起こるその**長さ**プロパティ関数に依存します。  
  
## <a name="example"></a>例  
 次の例では、使用、**長さ**プロパティ。  
  
```JavaScript  
function ArgTest(a, b){  
    var s = "";  
  
    s += "Expected Arguments: " + ArgTest.length;  
    s += "<br />";  
    s += "Passed Arguments: " + arguments.length;  
  
    return s;  
}  
  
document.write(ArgTest(1, 2));  
  
// Output:   
// Expected Arguments: 2  
// Passed Arguments: 2  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [arguments プロパティ (Function)](../../javascript/reference/arguments-property-function-javascript.md)   
 [length プロパティ (Array)](../../javascript/reference/length-property-array-javascript.md)   
 [length プロパティ (String)](../../javascript/reference/length-property-string-javascript.md)