---
title: sort メソッド (Array) (JavaScript) |Microsoft ドキュメント
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
- sort
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Sort method
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0462e60e623b99af458beb61eb7ef4215fe8ef41
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/05/2018
ms.locfileid: "28987816"
---
# <a name="sort-method-array-javascript"></a>sort メソッド (Array) (JavaScript)
並べ替え、`Array`です。  
  
## <a name="syntax"></a>構文  
  
```  
  
arrayobj.sort(sortFunction)   
```  
  
## <a name="parameters"></a>パラメーター  
 `arrayObj`  
 必須。 任意の `Array` オブジェクトを指定します。  
  
 `sortFunction`  
 任意。 要素の順序を決定するための関数の名前。 省略した場合、要素は ASCII 文字の順序の昇順で並べ替えられます。  
  
## <a name="return-value"></a>戻り値  
 並べ替えられた配列。  
  
## <a name="remarks"></a>コメント  
 `sort`メソッドの並べ替え、`Array`インプレース オブジェクト; いいえ新しい`Array`実行中にオブジェクトを作成します。  
  
 `sortFunction`2 つの引数を受け取るし、次の値のいずれかを返す必要があります。  
  
-   (0 より小さい)、負の値が小さいを最初の引数が渡された場合は 2 番目の引数よりもします。  最初の引数は、下限のインデックスに並べ替えられます。
  
-   ゼロ (0) 場合は 2 つの引数は同等です。  2 つの引数は、配列内の他の要素に対する並べ替えられますが、相互並べ替えは行われません。
  
-   (0 より大きい) 場合は、最初の引数が 2 番目の引数より大きい正の値。  2 番目の引数は、下限のインデックスに並べ替えられます。
  
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
  
## <a name="requirements"></a>必要条件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]