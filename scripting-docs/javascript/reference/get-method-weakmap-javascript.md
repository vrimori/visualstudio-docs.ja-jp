---
title: "get メソッド (WeakMap) (JavaScript) |Microsoft ドキュメント"
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
ms.assetid: d922c55d-486d-4feb-aedc-1f4867c417d2
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 29decb7e6a050188b75639eb7cf4f27494b31da2
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="get-method-weakmap-javascript"></a>get メソッド (WeakMap) (JavaScript)
指定した要素を `WeakMap` オブジェクトから戻します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
weakmapObj.get(key)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `weakmapObj`  
 必須です。 `WeakMap` オブジェクト。  
  
 `key`  
 必須です。 `WeakMap` 中の要素のキーです。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 キーに関連付けられているオブジェクトを戻します。 `WeakMap` にキーがない場合、このメソッドは `undefined` 値を戻します。  
  
## <a name="example"></a>例  
 次の例は、`WeakMap` オブジェクトからメンバーを取得する方法を示します。  
  
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
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]