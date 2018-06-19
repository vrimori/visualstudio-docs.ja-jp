---
title: has メソッド (Set) (JavaScript) |Microsoft ドキュメント
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
ms.assetid: fb80f2e0-fc5e-4508-af14-1c3b3b833636
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c9690e3d091e8ae0f9670fd737a29590524834c9
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636722"
---
# <a name="has-method-set-javascript"></a>has メソッド (Set) (JavaScript)
セットに指定された要素がある場合は `true` を戻します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
setObj.has(value)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `setObj`  
 必須です。 `Set` オブジェクト。  
  
 `value`  
 必須です。 テストする要素。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 セットに指定された要素がある場合は `true` です。  
  
## <a name="example"></a>例  
 次の例は、`Set` にメンバーを追加し、セット内の特定メンバーの存在を確認する方法を示します。  
  
```JavaScript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
  
document.write(s.has(1776));  
document.write(s.has("1776"));  
  
// Output:  
// true  
// false  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]