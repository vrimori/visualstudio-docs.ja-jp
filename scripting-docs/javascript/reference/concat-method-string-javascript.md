---
title: "concat メソッド (String) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: concat
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- concat method (String)
- Concat method
ms.assetid: 5d28ebb2-d534-4179-9297-a4c821ee9f24
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1b6419cc6404e06fc780802a30a3b4add8320881
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="concat-method-string-javascript"></a>concat メソッド (String) (JavaScript)
2 つ以上の文字列の連結を表す文字列を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
string1. concat([string2[, string3[, . . . [, stringN]]]])  
```  
  
## <a name="parameters"></a>パラメーター  
 `string1`  
 必須です。 `String`オブジェクトまたは文字列を他のすべてのリテラル文字列が連結されたを指定します。  
  
 `string2,. . ., stringN`  
 省略可能です。 文字列の末尾に追加する`string1`です。  
  
## <a name="remarks"></a>コメント  
 結果、`concat`メソッドは等価: `result`  =  `string1`  +  `string2`  +  `string3`  + `stringN`です。 ソースまたは結果の文字列内の値の変更は、他の文字列の値には影響しません。 任意の引数が文字列でない場合はまず文字列に変換に連結される前に`string1`です。  
  
## <a name="example"></a>例  
 次の例では、使用、`concat`メソッド (string) で使用する場合。  
  
```JavaScript  
var str1 = "ABCD"  
var str2 = "EFGH";  
var str3 = "1234";  
var str4 = "5678";  
document.write(str1.concat(str2, str3, str4));  
  
// Output: "ABCDEFGH12345678"  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用されます**:[文字列オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [加算演算子 (+)](../../javascript/reference/addition-operator-decrement-javascript.md)