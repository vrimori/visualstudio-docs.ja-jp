---
title: "Map オブジェクト (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- Map
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: a91dbcbe-f58d-41a0-be15-8c9d30020327
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d89890f9fecaf61e47e136734ed7fefb7b73cabd
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="map-object-javascript"></a>Map オブジェクト (JavaScript)
キーと値のペアのコレクションです。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
mapObj = new Map()  
```  
  
## <a name="remarks"></a>コメント  
 コレクション内のキーと値は、任意の型になります。 既存のキーを使用してコレクションに値を追加する場合、新しい値は元の値を置き換えます。  
  
## <a name="properties"></a>プロパティ  
 `Map` オブジェクトのプロパティを次の表に示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|[コンス トラクター](../../javascript/reference/constructor-property-map.md)|マップを作成する関数を指定します。|  
|[プロトタイプ](../../javascript/reference/prototype-property-map.md)|マップのプロトタイプへの参照を返します。|  
|[size](../../javascript/reference/size-property-map-javascript.md)|マップ内の要素数を返します。|  
  
## <a name="methods"></a>メソッド  
 `Map` オブジェクトのメソッドを次の表に示します。  
  
|メソッド|説明|  
|------------|-----------------|  
|[clear](../../javascript/reference/clear-method-map-javascript.md)|マップからすべての要素を削除します。|  
|[削除](../../javascript/reference/delete-method-map-javascript.md)|指定された要素をマップから削除します。|  
|[forEach](../../javascript/reference/foreach-method-map-javascript.md)|マップの各要素に対して、指定された処理を実行します。|  
|[get](../../javascript/reference/get-method-map-javascript.md)|指定された要素をマップから戻します。|  
|[が](../../javascript/reference/has-method-map-javascript.md)|マップが指定した要素を格納している場合、`true` を返します。|  
|[set](../../javascript/reference/set-method-map-javascript.md)|マップに新しい要素を追加します。|  
|[toString](../../javascript/reference/tostring-method-map-javascript.md)|マップの文字列表現を返します。|  
|[valueOf](../../javascript/reference/valueof-method-map-javascript.md)|指定されたオブジェクトのプリミティブ値を返します。|  
  
## <a name="example"></a>例  
 次の例は、メンバーを `Map` に追加して取得する方法を示します。  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
m.forEach(function (item, key, mapObj) {  
    document.write(item.toString() + "<br />");  
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