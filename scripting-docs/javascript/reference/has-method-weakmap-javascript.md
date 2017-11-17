---
title: "has メソッド (WeakMap) (JavaScript) |Microsoft ドキュメント"
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
ms.assetid: 12bedca1-bde7-413a-a4e2-06c03559044f
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e9a1706a1b96b5273ec280c4cef2be47a3bc6e17
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="has-method-weakmap-javascript"></a>has メソッド (WeakMap) (JavaScript)
`true` オブジェクトに指定された要素がある場合は `WeakMap` を戻します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
weakmapObj.has(key)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `weakmapObj`  
 必須です。 `WeakMap` オブジェクト。  
  
 `key`  
 必須です。 テストする要素のキー。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 `true` に指定したキーがある場合は、`WeakMap`。  
  
## <a name="example"></a>例  
 次の例は、`WeakMap` にメンバーを追加し、`has` を使用してそのメンバーの存在を確認する方法を示します。  
  
```JavaScript  
var dog = {  
    breed: "yorkie"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
  
document.write(wm.has(dog));  
  
// Output:  
// true  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]