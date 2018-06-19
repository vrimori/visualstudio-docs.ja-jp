---
title: get メソッド (Map) (JavaScript) |Microsoft ドキュメント
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
ms.assetid: bebbd6bc-6e61-4674-8196-7e907798973f
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 243d5aa93289cb7a13b34567b7824d028151bad3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636452"
---
# <a name="get-method-map-javascript"></a>get メソッド (Map) (JavaScript)
指定された要素をマップから戻します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
mapObj.get(key)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `mapObj`  
 必須です。 `Map` オブジェクト。  
  
 `key`  
 必須です。 `Map` 中の要素のキーです。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 キーに関連付けられているオブジェクトを戻します。 `Map` にキーがない場合、このメソッドは `undefined` 値を戻します。  
  
## <a name="example"></a>例  
 次の例は、`Map` オブジェクトから指定した要素を取得する方法を示します。  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
document.write(m.get(2));  
  
// Output:  
// red  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]