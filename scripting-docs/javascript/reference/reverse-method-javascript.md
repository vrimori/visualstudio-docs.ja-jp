---
title: reverse メソッド (JavaScript) |Microsoft ドキュメント
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
- reverse
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- arrays [Visual Studio], reversing elements
- reverse method
- transposing elements
ms.assetid: 02ab051b-79b8-4646-b502-381671e78c12
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9a34385ccf89557688698b50384b3dfe359478df
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639712"
---
# <a name="reverse-method-javascript"></a>reverse メソッド (JavaScript)
内の要素を反転する`Array`です。  
  
## <a name="syntax"></a>構文  
  
```  
  
arrayObj.reverse()   
```  
  
## <a name="parameters"></a>パラメーター  
 `arrayObj`  
 必須です。 任意の `Array` オブジェクトを指定します。  
  
## <a name="return-value"></a>戻り値  
 逆順の配列。  
  
## <a name="remarks"></a>コメント  
 必要な`arrayObj`参照は、`Array`オブジェクト。  
  
 `reverse`メソッドの要素を反転させます、`Array`インプレース オブジェクト。 作成されません新しい`Array`オブジェクトの実行中にします。  
  
 配列は、連続したがない場合、`reverse`メソッドは、配列内のギャップを配列内の要素を作成します。 値を持つ要素を作成してこれらの各`undefined`です。  
  
## <a name="example"></a>例  
 `reverse` メソッドの使用例を次に示します。  
  
```JavaScript  
var arr = new Array(0,1,2,3,4);   
var reverseArr = arr.reverse();  
document.write(reverseArr);  
  
// Output:  
// 4,3,2,1,0  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [concat メソッド (Array)](../../javascript/reference/concat-method-array-javascript.md)