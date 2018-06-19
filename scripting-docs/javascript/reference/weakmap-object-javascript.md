---
title: WeakMap オブジェクト (JavaScript) |Microsoft ドキュメント
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
- WeakMap
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4682d2dc-caf9-4fa8-8313-a0a0b804fd1d
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8de97f8acb94921090696e9019a1df5d945db7c6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641742"
---
# <a name="weakmap-object-javascript"></a>WeakMap オブジェクト (JavaScript)
各キーがオブジェクトの参照である、キーと値のペアのコレクション。  
  
## <a name="syntax"></a>構文  
  
```  
weakmapObj = new WeakMap()  
```  
  
## <a name="remarks"></a>コメント  
 `WeakMap` オブジェクトは列挙できません。  
  
 既存のキーを使用してコレクションに値を追加する場合、新しい値は元の値を置き換えます。  
  
 `WeakMap`オブジェクトのキー オブジェクトへの参照が「弱い」です。 これは、`WeakMap` がキー オブジェクトに発生するガベージ コレクションを阻止できないことを意味します。 キー オブジェクトへの参照 (`WeakMap` 以外の参照) がない場合、ガベージ コレクターはキー オブジェクトを収集することがあります。  
  
## <a name="properties"></a>プロパティ  
 `WeakMap` オブジェクトのプロパティを次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|[コンス トラクター](../../javascript/reference/constructor-property-weakmap.md)|`WeakMap` を作成する関数を指定します。|  
|[プロトタイプ](../../javascript/reference/prototype-property-weakmap.md)|`WeakMap` のプロトタイプへの参照を返します。|  
  
## <a name="methods"></a>メソッド  
 `WeakMap` オブジェクトのメソッドを次の表に示します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[clear](../../javascript/reference/clear-method-weakmap-javascript.md)|
          `WeakMap` からすべての要素を削除します。|  
|[削除](../../javascript/reference/delete-method-weakmap-javascript.md)|指定された要素を `WeakMap` から削除します。|  
|[get](../../javascript/reference/get-method-weakmap-javascript.md)|指定された要素を `WeakMap` から戻します。|  
|[が](../../javascript/reference/has-method-weakmap-javascript.md)|`true` が指定した要素を格納している場合、`WeakMap` を返します。|  
|[set](../../javascript/reference/set-method-weakmap-javascript.md)|`WeakMap` オブジェクトに新しい要素を追加します。|  
|[toString](../../javascript/reference/tostring-method-weakmap-javascript.md)|`WeakMap` の文字列表現を返します。|  
|[valueOf](../../javascript/reference/valueof-method-weakmap-javascript.md)|指定されたオブジェクトのプリミティブ値を返します。|  
  
## <a name="example"></a>例  
 次の例は、メンバーを `WeakMap` オブジェクトに追加して取得する方法を示します。  
  
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