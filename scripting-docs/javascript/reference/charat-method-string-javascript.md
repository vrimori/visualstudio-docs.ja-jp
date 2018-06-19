---
title: charAt メソッド (String) (JavaScript) |Microsoft ドキュメント
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
- charAt
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- String object, returning characters
- charAt method
- characters, returning part of
ms.assetid: 63173e15-17f6-47c5-8f94-98ef1eb04c1a
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 201d85fec4ba184f0842c7401d986650b9ee078c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24634132"
---
# <a name="charat-method-string-javascript"></a>charAt メソッド (String) (JavaScript)
指定されたインデックス番号の位置にある文字を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
strObj. charAt(index)  
```  
  
## <a name="parameters"></a>パラメーター  
 `strObj`  
 必須です。 どの`String`オブジェクトまたは文字列リテラルです。  
  
 `index`  
 必須です。 目的の文字の 0 から始まるインデックス。  
  
## <a name="remarks"></a>コメント  
 `charAt`メソッドが、指定した位置にある文字と等しい文字の値を返します`index`です。 文字列の最初の文字インデックス 0 には、2 つ目はインデックス 1 など。 値を`index`が範囲外に戻り値、空の文字列。  
  
## <a name="example"></a>例  
 次の例では、使用、`charAt`メソッド。  
  
```JavaScript  
var str = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";  
document.write(str.charAt(str.length - 1));  
  
// Output: Z  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用されます**:[文字列オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)