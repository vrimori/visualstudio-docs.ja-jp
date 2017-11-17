---
title: "add メソッド (WeakSet) (JavaScript) |Microsoft ドキュメント"
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
ms.assetid: d35d0287-6b33-4720-b9d7-8954c428ce4e
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3ab486beaba4a26c73930b5ceaee927f73aa077a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="add-method-weakset-javascript"></a>add メソッド (WeakSet) (JavaScript)
`WeakSet` オブジェクトに新しい要素を追加します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
weaksetObj.add(obj)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `weaksetObj`  
 必須です。 `WeakSet` オブジェクト。  
  
 `obj`  
 必須です。 `WeakSet` の新しい要素を指定します。  
  
## <a name="remarks"></a>コメント  
 新しい要素は、任意の値ではなくオブジェクトで、なおかつ一意でなければなりません。 `WeakSet` に一意でない要素を追加する場合、新しい要素はコレクションに追加されません。  
  
## <a name="example"></a>例  
 次の例は、メンバーをセットに追加し、その後、メンバーが追加されたことを確認する方法を示しています。  
  
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