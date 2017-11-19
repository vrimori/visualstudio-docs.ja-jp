---
title: "lastIndexOf メソッド (Array) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [JavaScript], lastIndexOf method
- lastIndexOf method [JavaScript]
ms.assetid: 04f5145d-007e-498f-b06f-11ab384c2968
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12d2a0fca7a7cd82543a83ea19aca49d3cbb93b6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="lastindexof-method-array-javascript"></a>lastIndexOf メソッド (Array) (JavaScript)
指定した値が配列内で最後に見つかった位置のインデックスを返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
array1.lastIndexOf(searchElement[, fromIndex])  
```  
  
#### <a name="parameters"></a>パラメーター  
  
|パラメーター|定義|  
|---------------|----------------|  
|`array1`|必須です。 検索する配列オブジェクト。|  
|`searchElement`|必須です。 内で検索する値`array1`です。|  
|`fromIndex`|省略可能です。 検索を開始する位置を示す配列のインデックス。 場合`fromIndex`は省略すると、検索は、配列内の最後のインデックスから開始します。|  
  
## <a name="return-value"></a>戻り値  
 最後に見つかった位置のインデックス`searchElement`、配列の場合は-1`searchElement`が見つかりません。  
  
## <a name="remarks"></a>コメント  
 `lastIndexOf`メソッドは、指定した値の配列を検索します。 メソッドは、指定した値が見つからない場合に、最初に見つかった位置のインデックスを返します。  
  
 検索はインデックスを降順で発生 (最後のメンバーの最初)。 昇順で検索するには、使用、 [indexOf メソッド (Array)](../../javascript/reference/indexof-method-array-javascript.md)です。  
  
 配列要素を比較する、`searchElement`値厳密等価、による比較に似ていますが、`===`演算子。 詳細については、次を参照してください。[比較演算子](../../javascript/reference/comparison-operators-javascript.md)です。  
  
 省略可能な`fromIndex`引数は、検索を開始する位置を示す配列インデックスを指定します。 場合`fromIndex`がより大きいまたは配列の長さと等しい、配列全体が検索されます。 場合`fromIndex`はプラスの配列の長さに負の場合、検索開始`fromIndex`です。 計算されたインデックスが 0 未満の場合は、-1 が返されます。  
  
## <a name="example"></a>例  
 次の例では、使用、`lastIndexOf`メソッドです。  
  
```JavaScript  
// Create an array.  
var ar = ["ab", "cd", "ef", "ab", "cd"];  
  
// Determine the first location, in descending order, of "cd".  
document.write(ar.lastIndexOf("cd") + "<br/>");  
  
// Output: 4  
  
// Find "cd" in descending order, starting at index 2.  
document.write(ar.lastIndexOf("cd", 2) + "<br/>");  
  
// Output: 1  
  
// Search for "gh" (which is not found).  
document.write(ar.lastIndexOf("gh")+ "<br/>");  
  
// Output: -1  
  
// Find "ab" with a fromIndex argument of -3.  
// The search in descending order starts at index 3,  
// which is the array length minus 2.  
document.write(ar.lastIndexOf("ab", -3) + "<br/>");  
// Output: 0  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [indexOf メソッド (Array)](../../javascript/reference/indexof-method-array-javascript.md)   
 [Array オブジェクト](../../javascript/reference/array-object-javascript.md)   
 [配列の使用](../../javascript/advanced/using-arrays-javascript.md)