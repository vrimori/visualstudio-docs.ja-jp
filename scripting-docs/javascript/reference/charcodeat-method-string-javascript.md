---
title: "charCodeAt メソッド (String) (JavaScript) |Microsoft ドキュメント"
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
- charCodeAt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- charCodeAt method
ms.assetid: 5b0290a7-ee4d-4738-a909-c02ef64a2f1a
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8e7b8e62dfd29aa42d9816d0c5e27cc90440751a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="charcodeat-method-string-javascript"></a>charCodeAt メソッド (String) (JavaScript)
指定した位置にある文字の Unicode 値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
strObj. charCodeAt(index)  
```  
  
## <a name="parameters"></a>パラメーター  
 `strObj`  
 必須です。 どの`String`オブジェクトまたは文字列リテラルです。  
  
 `index`  
 必須です。 目的の文字の 0 から始まるインデックス。 指定したインデックス位置の文字がない場合`NaN`が返されます。  
  
## <a name="remarks"></a>コメント  
  
## <a name="example"></a>例  
 `charCodeAt` メソッドの使用例を次に示します。  
  
```JavaScript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";   
document.write(str.charCodeAt(str.length - 1));  
  
// Output: 90   
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [String.fromCharCode 関数](../../javascript/reference/string-fromcharcode-function-javascript.md)