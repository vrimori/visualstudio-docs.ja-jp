---
title: "delete メソッド (Map) (JavaScript) |Microsoft ドキュメント"
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
ms.assetid: a073e1a1-5862-485b-b2bd-26c66a3aff51
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5185b883cf603acdc91fe1f1c833d337c4468ba4
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="delete-method-map-javascript"></a>delete メソッド (Map) (JavaScript)
指定された要素をマップから削除します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
mapObj.delete(key)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `mapObj`  
 必須です。 `Map` オブジェクト。  
  
 `key`  
 必須です。 削除する要素のキー。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 `true` の場合、要素は既に削除されています。  
  
## <a name="example"></a>例  
 次の例は、メンバーを `Map` に追加して、その 1 つを削除する方法を示します。  
  
```JavaScript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.delete(1);  
  
m.forEach(function (item) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// red  
// 2  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]