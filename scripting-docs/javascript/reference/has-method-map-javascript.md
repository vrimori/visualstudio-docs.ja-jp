---
title: has メソッド (Map) (JavaScript) |Microsoft ドキュメント
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
ms.assetid: 876df854-2941-4db2-92c6-1b497840b169
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 48228b495c845bef91caa0b85e67980100a6f790
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636712"
---
# <a name="has-method-map-javascript"></a>has メソッド (Map) (JavaScript)
マップに指定された要素がある場合は `true` を戻します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
mapObj.has(key)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `mapObj`  
 必須です。 `Map` オブジェクト。  
  
 `key`  
 必須です。 テストする要素のキー。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 マップに指定された要素がある場合は `true` です。  
  
## <a name="example"></a>例  
 次の例は、`Map` にメンバーを追加し、マップ内のそのメンバーの存在を確認する方法を示します。  
  
```JavaScript  
var m = new Map();  
m.set(2, "red");  
  
document.write(m.has(2));  
  
// Output:  
// true  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]