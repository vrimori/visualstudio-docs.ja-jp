---
title: "prototype プロパティ (Object) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: Prototype
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- inheritance, objects
- Prototype property
ms.assetid: 9fc434a1-5995-4fcb-a4e8-00e7f615aaa2
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a73d213b6b17f5046eb1f4c498aeb223f942f2d8
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="prototype-property-object-javascript"></a>prototype プロパティ (Object) (JavaScript)
指定されたオブジェクトのクラスのプロトタイプへの参照を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
objectName.prototype  
```  
  
## <a name="remarks"></a>コメント  
 `objectName` 引数は、オブジェクトの名前です。  
  
 `prototype` プロパティを使用すると、オブジェクトのクラスが持つ機能の基本セットを知ることができます。 オブジェクトの新しいインスタンスは、そのオブジェクトに割り当てられているプロトタイプの機能を "継承" します。  
  
 たとえば、`Array` オブジェクトに配列で最も大きな要素の値を返すメソッドを追加する場合は、関数を宣言して `Array.prototype` に追加してから使用します。  
  
```JavaScript  
function array_max( ){  
    var i, max = this[0];  
    for (i = 1; i < this.length; i++)  
    {  
    if (max < this[i])  
    max = this[i];  
    }  
    return max;  
}  
Array.prototype.max = array_max;  
var myArray = new Array(7, 1, 3, 11, 25, 9  
);  
document.write(myArray.max());  
  
// Output:  
// 25  
  
```  
  
 すべての組み込み[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]オブジェクトが、`prototype`プロパティは読み取り専用です。 プロトタイプへのプロパティとメソッドを追加する可能性がありますが、オブジェクトが別のプロトタイプを割り当てられていない可能性があります。 ただし、ユーザー定義オブジェクトには、新しいプロトタイプを割り当てることがあります。  
  
 この言語リファレンスにおける組み込みオブジェクトごとに、メソッドおよびプロパティの一覧は、どのパーツが、オブジェクトのプロトタイプの一部とされていないを示します。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [constructor プロパティ (Object)](../../javascript/reference/constructor-property-object-javascript.md)