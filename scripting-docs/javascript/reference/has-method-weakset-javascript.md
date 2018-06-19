---
title: has メソッド (WeakSet) (JavaScript) |Microsoft ドキュメント
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
ms.assetid: e24f0876-26bd-4007-b12a-360bb6fa0951
caps.latest.revision: 2
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0dbc7e17e3fd73730386293c5e3f894455e41a93
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637012"
---
# <a name="has-method-weakset-javascript"></a>has メソッド (WeakSet) (JavaScript)
指定された要素が `WeakSet` にある場合は `true` を返します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
setObj.has(obj)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `setObj`  
 必須です。 `WeakSet` オブジェクト。  
  
 `obj`  
 必須です。 テストする要素。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 セットに指定された要素がある場合は `true` です。  
  
## <a name="example"></a>例  
 次の例は、`WeakSet` にメンバーを追加し、セット内の特定メンバーの存在を確認する方法を示します。  
  
```JavaScript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]