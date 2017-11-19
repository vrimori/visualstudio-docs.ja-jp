---
title: "concat メソッド (Array) (JavaScript) |Microsoft ドキュメント"
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
- concat method (array)
- Concat method
ms.assetid: bc2b4a6a-209e-4d59-8c24-59db01d53b1e
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 19f3a216a36f9ad8c422036476e46b89b6ee488c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="concat-method-array-javascript"></a>concat メソッド (Array) (JavaScript)
2 つ以上の配列を結合します。  
  
## <a name="syntax"></a>構文  
  
```  
  
array1.concat([item1[, item2[, . . . [, itemN]]]])   
```  
  
## <a name="parameters"></a>パラメーター  
 `array1`  
 必須です。 `Array`オブジェクトを他の配列が連結されます。  
  
 `item1,. . ., itemN`  
 省略可能です。 末尾に追加する項目を`array1`です。  
  
## <a name="remarks"></a>コメント  
 `concat`メソッドを返します、`Array`を連結したものを含むオブジェクトを`array1`およびその他の指定された項目。  
  
 追加するアイテム (*item1 itemN*)、配列には、順序で追加された、リストの最初の項目から開始します。 末尾にその内容を追加、項目のいずれかが、配列、`array1`です。 項目が配列以外の場合は、1 つの配列要素として、配列の末尾に追加されます。  
  
 ソース配列の要素は、次のように、結果の配列にコピーされます。  
  
-   オブジェクトは、新しい配列に連結されている配列のいずれかからコピーが、オブジェクト参照は、同じオブジェクトを指す続行します。 新しい配列と、元の配列のいずれかの変更を他の変更になります。  
  
-   新しい配列に数値または文字列の値を追加する場合、値のみがコピーされます。 配列は 1 つの値を変更しても、もう一方の値には影響しません。  
  
## <a name="example"></a>例  
 次の例を使用する方法を示しています、`concat`メソッド配列で使用する場合。  
  
```JavaScript  
var a, b, c, d;  
a = new Array(1,2,3);  
b = "dog";  
c = new Array(42, "cat");  
d = a.concat(b, c);  
document.write(d);  
  
//Output:   
1, 2, 3, "dog", 42, "cat"  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [concat メソッド (String)](../../javascript/reference/concat-method-string-javascript.md)   
 [join メソッド (Array)](../../javascript/reference/join-method-array-javascript.md)