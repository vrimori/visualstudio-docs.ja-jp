---
title: "sort メソッド (Array) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: sort
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: Sort method
ms.assetid: 9bd8b54a-c838-4806-85c8-62eebe6bc48c
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2d098b47591ca7bbb4e3e8da5e5c14f8c0e9b255
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="sort-method-array-javascript"></a>sort メソッド (Array) (JavaScript)
並べ替え、`Array`です。  
  
## <a name="syntax"></a>構文  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## <a name="parameters"></a>パラメーター  
 `arrayObj`  
 必須です。 任意の `Array` オブジェクトを指定します。  
  
 `sortFunction`  
 省略可能です。 要素の順序を決定するための関数の名前。 省略した場合、要素は ASCII 文字の順序の昇順で並べ替えられます。  
  
## <a name="return-value"></a>戻り値  
 並べ替えられた配列。  
  
## <a name="remarks"></a>コメント  
 `sort`メソッドの並べ替え、`Array`インプレース オブジェクト; いいえ新しい`Array`実行中にオブジェクトを作成します。  
  
 内の関数を指定する場合、`sortFunction`引数を返す必要があります、次の値のいずれか。  
  
-   負の値を使用している場合は、渡される最初の引数が 2 番目の引数未満です。  
  
-   2 つの引数が等しい場合は 0 を返します。  
  
-   最初の引数が 2 番目の引数より大きい場合は、正値です。  
  
## <a name="example"></a>例  
 `sort` メソッドを使用する方法の例を次に示します。  
  
```JavaScript  
var a = new Array(4, 11, 2, 10, 3, 1);  
  
var b = a.sort();  
document.write(b);  
document.write("<br/>");  
  
// This is ASCII character order.  
// Output: 1,10,11,2,3,4)  
  
// Sort the array elements with a function that compares array elements.  
b = a.sort(CompareForSort);  
document.write(b);  
document.write("<br/>");  
// Output: 1,2,3,4,10,11.  
  
// Sorts array elements in ascending order numerically.  
function CompareForSort(first, second)  
{  
    if (first == second)  
        return 0;  
    if (first < second)  
        return -1;  
    else  
        return 1;   
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]