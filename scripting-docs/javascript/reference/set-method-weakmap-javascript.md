---
title: set メソッド (WeakMap) (JavaScript) |Microsoft ドキュメント
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
ms.assetid: 29fc72b1-224f-4f19-8c06-5d926d695b03
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c916bda13c7bd973b37c4e4cb6b81e327ee5de54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639602"
---
# <a name="set-method-weakmap-javascript"></a>set メソッド (WeakMap) (JavaScript)
`WeakMap` オブジェクトに新しい要素を追加します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
weakmapObj.set(key, value)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `weakmapObj`  
 必須です。 `WeakMap` オブジェクト。  
  
 `key`  
 必須です。 追加する要素のキーを表すオブジェクト。 これは、オブジェクト参照である必要があります。  
  
 `value`  
 必須です。 追加する要素の値。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 新しいキーと値のペアのある `WeakMap` オブジェクトを戻します。  
  
## <a name="remarks"></a>コメント  
 既存のキーを使用してコレクションに値を追加する場合、新しい値は元の値を置き換えます。  
  
## <a name="example"></a>例  
 次の例は、`WeakMap` オブジェクトにメンバーを追加する方法を示します。  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]