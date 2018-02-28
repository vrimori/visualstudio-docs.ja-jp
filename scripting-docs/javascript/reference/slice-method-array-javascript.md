---
title: "slice メソッド (Array) (JavaScript) |Microsoft ドキュメント"
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
- slice
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- zero-based index
- Array object
- slice method
ms.assetid: 3c122219-14de-4126-b091-809659c026d6
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a61cd331abef9d1a0d979f547f6d6f12222c1eee
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="slice-method-array-javascript"></a>slice メソッド (Array) (JavaScript)
配列の一部を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
arrayObj.slice(start, [end])   
```  
  
## <a name="parameters"></a>パラメーター  
 `arrayObj`  
 必須です。 `Array` オブジェクト。  
  
 `start`  
 必須です。 指定した部分の先頭`arrayObj`です。  
  
 `end`  
 省略可能です。 指定した部分の末尾`arrayObj`です。  
  
## <a name="remarks"></a>コメント  
 `slice`メソッドを返します、`Array`オブジェクトの指定部分を含む`arrayObj`です。  
  
 `slice`メソッドを含めずによって示される要素をコピー`end`です。 場合`start`は負の値として扱われます`length`  + `start`ここで、`length`配列の長さです。 場合`end`は負の値として扱われます`length`  +  `end`場所`length`配列の長さです。 `end` が省略されている場合は、`arrayObj` の最後まで抽出を継続します。 場合`end`の前に発生`start`、新しい配列に要素はコピーされません。  
  
## <a name="example"></a>例  
 `slice` メソッドを使用する方法の例を次に示します。 最後の要素以外はすべて、最初の例で`myArray`にコピーされる`newArray`です。 2 番目の例の最後の 2 つの要素のみ`myArray`にコピーされます`newArray`です。  
  
```JavaScript  
var origArray = [3, 5, 7, 9];  
var newArray = origArray. slice(0, -1);  
document.write(origArray);  
document.write("<br/>");  
newArray = origArray. slice(-2);  
document.write(newArray);  
  
// Output:  
// 3,5,7,9  
// 7,9  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [slice メソッド (String)](../../javascript/reference/slice-method-string-javascript.md)   
 [String オブジェクト](../../javascript/reference/string-object-javascript.md)