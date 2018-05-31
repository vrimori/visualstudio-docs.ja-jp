---
title: forEach メソッド (Map) (JavaScript) |Microsoft ドキュメント
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
ms.assetid: 9cdf0adc-77c7-4407-8ba7-ada0fb09e507
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 549d7d625fb4dfe88b2db69e6aa0ff66c7e90f66
ms.sourcegitcommit: 37144589d9f850ff81ec7bfb884429989925a43d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2018
ms.locfileid: "34335802"
---
# <a name="foreach-method-map-javascript"></a>forEach メソッド (Map) (JavaScript)
マップの各要素に対して、指定された処理を実行します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
mapObj.forEach(callbackfn[, thisArg])  
```  
  
#### <a name="parameters"></a>パラメーター  
 `mapObj`  
 必須。 `Map` オブジェクト。  
  
 `callbackfn`  
 必須。 `forEach` がマップ内の各要素に対して 1 回呼び出す関数。 `callbackfn` 最大 3 つの引数を受け取ります。 `forEach` は、マップ内の各要素に対して `callbackfn` 関数を 1 回呼び出します。  
  
 `thisArg`  
 任意。 `this` キーワードが `callbackfn` 関数内で参照できるオブジェクト。 `thisArg` を省略すると、`undefined` が `this` 値として使用されます。  
  
## <a name="exceptions"></a>例外  
 `callbackfn` 引数が関数オブジェクトではない場合は、`TypeError` 例外がスローされます。  
  
## <a name="remarks"></a>コメント  
 コールバック関数の構文は次のとおりです。  
  
 `function callbackfn(value, key, mapObj)`  
  
 コールバック関数は、次の表に示すパラメーターを最大 3 つ使用して宣言できます。  
  
|コールバック引数|定義|  
|-----------------------|----------------|  
|`value`|マップに格納された値。|  
|`key`|マップに格納されたキー。|  
|`mapObj`|走査する `Map` オブジェクト。|  
  
## <a name="example"></a>例  
 次の例は、`Map` を使用して `forEach` のメンバーを取得する方法を示します。  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (value, key, mapObj) {  
    document.write(value.toString() + "<br />");  
});  
  
document.write("<br />");  
document.write(m.get(2));  
  
// Output:  
// black  
// red  
// 2  
// 3  
//  
// red  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]
