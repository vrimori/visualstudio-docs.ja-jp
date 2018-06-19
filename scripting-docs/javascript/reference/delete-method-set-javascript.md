---
title: delete メソッド (Set) (JavaScript) |Microsoft ドキュメント
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
ms.assetid: 052c409e-10c9-49f2-955d-5ad7e31c14f3
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 72762b93c6996fd72bd035c5d653f0e85f4ffd33
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636092"
---
# <a name="delete-method-set-javascript"></a>delete メソッド (Set) (JavaScript)
指定された要素をセットから削除します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
setObj.delete(value)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `setObj`  
 必須です。 `Set` オブジェクト。  
  
 `value`  
 必須です。 削除する要素。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 `true` の場合、要素は既に削除されています。  
  
## <a name="example"></a>例  
 次の例は、メンバーを `Set` に追加して、その 1 つを削除する方法を示します。  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
s.delete("founding father");  
  
s.forEach(function (item) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776,  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]