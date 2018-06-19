---
title: slice メソッド (String) (JavaScript) |Microsoft ドキュメント
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
- slice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- strings [Visual Studio], returning characters
- slice method
ms.assetid: 80cd77a6-3718-492e-8e96-f909d8721d91
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1baa0a05a2d6aa8c06cc962761c8e557632d034c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641032"
---
# <a name="slice-method-string-javascript"></a>slice メソッド (String) (JavaScript)
文字列の一部分を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
stringObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>パラメーター  
 `stringObj`  
 必須です。 `String` オブジェクトまたは文字列リテラル。  
  
 `start`  
 必須です。 インデックスの指定した部分の先頭に`stringObj`です。  
  
 `end`  
 省略可能です。 インデックスの指定した部分の末尾に`stringObj`です。 最大の部分文字列に文字が含まれていますを含めないことで示される文字`end`です。 この値が指定されていない場合、部分文字列末尾まで続きますの`stringObj`します。  
  
## <a name="remarks"></a>コメント  
 `slice`メソッドを返します、`String`オブジェクトの指定部分を含む`stringObj`です。  
  
 `slice`メソッドまでを含めずによって示される文字のコピー`end`です。  
  
 場合`start`は負の値として扱われます*長さ* +  `start`場所*長さ*文字列の長さです。 場合`end`は負の値として扱われます*長さ* + `end`です。 場合`end`は省略すると、コピーの末尾には続行されます`stringObj`です。 場合`end`の前に発生`start`、新しい文字列に文字はコピーされません。  
  
## <a name="example"></a>例  
 最初の例では、`slice`メソッド全体の文字列を返します。 2 番目の例では、`slice`メソッドには、最後の文字を除く文字列全体が返されます。  
  
```JavaScript  
var str1 = "all good boys do fine";  
  
var slice1 = str1.slice(0);  
var slice2 = str1.slice(0,-1);  
var slice3 = str1.slice(4);  
var slice4 = str1.slice(4, 8);  
  
document.write(slice1 + "<br/>");  
document.write(slice2 + "<br/>");  
document.write(slice3 + "<br/>");  
document.write(slice4);  
  
// Output:  
// all good boys do fine  
// all good boys do fin  
// good boys do fine  
// good  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用されます**:[文字列オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [slice メソッド (Array)](../../javascript/reference/slice-method-array-javascript.md)