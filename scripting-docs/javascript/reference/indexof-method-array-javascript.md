---
title: indexOf メソッド (Array) (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [JavaScript], indexOf method
- indexOf method [JavaScript]
ms.assetid: 5bee31ae-aaf1-4466-8cfd-ed287e3cdf17
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 63685219faf42991da6b798493c58b356ab97279
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637482"
---
# <a name="indexof-method-array-javascript"></a>indexOf メソッド (Array) (JavaScript)
ある値が配列内で最初に見つかった位置のインデックスを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
array1.indexOf(searchElement[, fromIndex])  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|定義|  
|---------------|----------------|  
|`array1`|必須です。 配列オブジェクト。|  
|`searchElement`|必須です。 内で検索する値`array1`です。|  
|`fromIndex`|省略可能です。 検索を開始する位置を示す配列のインデックス。 場合`fromIndex`は省略すると、検索はインデックス 0 から開始します。|  
  
## <a name="return-value"></a>戻り値  
 最初に見つかった位置のインデックス`searchElement`、配列の場合は-1`searchElement`が見つかりません。  
  
## <a name="remarks"></a>コメント  
 `indexOf`メソッドは、指定した値の配列を検索します。 メソッドは、指定した値が見つからない場合に、最初に見つかった位置のインデックスを返します。  
  
 検索は、インデックスの昇順で発生します。  
  
 配列要素を比較する、`searchElement`値厳密等価に似ていますが、`===`演算子。 詳細については、次を参照してください。[比較演算子](../../javascript/reference/comparison-operators-javascript.md)です。  
  
 省略可能な`fromIndex`引数は、検索を開始する位置を示す配列インデックスを指定します。 場合`fromIndex`がより大きいまたは等しい、配列の長さ、-1 が返されます。 場合`fromIndex`はプラスの配列の長さに負の場合、検索開始`fromIndex`です。  
  
## <a name="example"></a>例  
 次の例では、使用、`indexOf`メソッドです。  
  
```JavaScript  
// Create an array. (The elements start at index 0.)  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location of "cd".  
document.write(ar.indexOf("cd") + "<br/>");  
  
// Output: 1  
  
// Find "cd" starting at index 2.  
document.write(ar.indexOf("cd", 2) + "<br/>");  
  
// Output: 4  
  
// Find "gh" (which is not found).  
document.write (ar.indexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -2.  
// The search starts at index 3, which is the array length plus -2.  
document.write (ar.indexOf("ab", -2) + "<br/>");  
// Output: 3  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [JavaScript メソッド](../../javascript/reference/javascript-methods.md)   
 [Array オブジェクト](../../javascript/reference/array-object-javascript.md)   
 [配列の使用](../../javascript/advanced/using-arrays-javascript.md)