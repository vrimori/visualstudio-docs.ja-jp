---
title: propertyIsEnumerable メソッド (Object) (JavaScript) |Microsoft ドキュメント
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
- propertyIsEnumerable
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- propertyIsEnumerable property
ms.assetid: d90c7c2e-ea23-4710-a957-9aefbbd1f68b
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5664732db6a311586f11eb13eee4407fdf81410f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24638852"
---
# <a name="propertyisenumerable-method-object-javascript"></a>propertyIsEnumerable メソッド (Object) (JavaScript)
指定したプロパティが列挙可能かどうかを判断します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object. propertyIsEnumerable(proName)  
```  
  
## <a name="parameters"></a>パラメーター  
 `object`  
 必須です。 オブジェクトのインスタンスを指定します。  
  
 `proName`  
 必須です。 プロパティ名の文字列値を指定します。  
  
## <a name="remarks"></a>コメント  
 `propertyIsEnumerable`メソッドを返します。`true`場合`proName`内に存在する`object`を使用して列挙すると、`For`ループします。 `propertyIsEnumerable`メソッドを返します。`false`場合`object`は指定した名前のプロパティがありません、または指定したプロパティは、列挙可能な場合です。 通常、定義済みのプロパティはありませんが、列挙可能なユーザー定義プロパティ常に列挙可能です。  
  
 `propertyIsEnumerable`メソッドは、プロトタイプ チェーン内のオブジェクトと見なしません。  
  
## <a name="example"></a>例  
  
```JavaScript  
var a = new Array("apple", "banana", "cactus");  
document.write(a.propertyIsEnumerable(1));  
  
// Output: true  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [prototype プロパティ (Object)](../../javascript/reference/prototype-property-object-javascript.md)