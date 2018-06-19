---
title: delete メソッド (WeakMap) (JavaScript) |Microsoft ドキュメント
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
ms.assetid: 7d54ae55-e514-45ba-b403-d1eee46837d2
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd4cec06b77b7198e23d7e455849b5c0bf6d7ff9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636332"
---
# <a name="delete-method-weakmap-javascript"></a>delete メソッド (WeakMap) (JavaScript)
`WeakMap` オブジェクトから指定された要素を削除します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
weakmapObj.delete(key)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `weakmapObj`  
 必須です。 `WeakMap` オブジェクト。  
  
 `key`  
 必須です。 削除する要素のキー。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 `true` の場合、要素は既に削除されています。  
  
## <a name="example"></a>例  
 次の例は、`WeakMap` にメンバーを追加して削除する方法を示します。  
  
```JavaScript  
function Dog(breed) {  
    this.breed = breed;  
}  
  
var dog = new Dog("yorkie");  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.delete(dog);  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]