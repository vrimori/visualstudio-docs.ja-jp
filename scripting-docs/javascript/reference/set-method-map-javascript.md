---
title: set メソッド (Map) (JavaScript) |Microsoft ドキュメント
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
ms.assetid: 31ee71a0-b09d-442a-9e02-825accf94ffa
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a84a5b2714fde55fba03d581faa851d7245e001
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24639432"
---
# <a name="set-method-map-javascript"></a>set メソッド (Map) (JavaScript)
マップに新しい要素を追加します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
mapObj.set(key, value)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `mapObj`  
 必須です。 `Map` オブジェクト。  
  
 `key`  
 必須です。 新しい要素のキー。  
  
 `value`  
 必須です。 追加する要素の値。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 新しいキーと値のペアのある `Map` オブジェクトを戻します。  
  
## <a name="remarks"></a>コメント  
 既存のキーを使用してコレクションに値を追加する場合、新しい値は元の値を置き換えます。  
  
## <a name="example"></a>例  
 次の例は、メンバーを `Map` に追加して取得する方法を示します。  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// black  
// red  
// 2  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]