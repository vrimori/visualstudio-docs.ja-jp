---
title: Object.setPrototypeOf 関数 (JavaScript) |Microsoft ドキュメント
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
ms.assetid: a2609f6e-aeee-4c13-b7cf-c31ddf58ff35
caps.latest.revision: 3
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a2ae28420893cd49691c1a6ac50fe5896700947
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2018
ms.locfileid: "29900839"
---
# <a name="objectsetprototypeof-function-javascript"></a>Object.setPrototypeOf 関数 (JavaScript)
オブジェクトのプロトタイプを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
Object.setPrototypeOf(obj, proto);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `obj`  
 必須。 プロトタイプを設定する対象のオブジェクト。  
  
 `proto`  
 必須。 新しいプロトタイプ オブジェクト。  
  
## <a name="remarks"></a>コメント  
  
> [!WARNING]
>  プロトタイプを設定すると、プロトタイプが変更されたオブジェクトにアクセスするすべての JavaScript コードでパフォーマンスが低下する可能性があります。  
  
## <a name="example"></a>例  
 オブジェクトのプロトタイプを設定する方法のコード例を次に示します。  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(Object.getPrototypeOf(rec) === Rectangle.prototype);  // Returns true  
    Object.setPrototypeOf(rec, Object.prototype);  
    console.log(Object.getPrototypeOf(rec) === Rectangle.prototype);  // Returns false  
}  
```  
  
## <a name="example"></a>例  
 次のコード例は、プロパティをプロトタイプに追加することによってオブジェクトに追加する方法を示しています。  
  
```JavaScript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
Object.setPrototypeOf(obj, proto);  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## <a name="example"></a>例  
 次のコード例では、`String` オブジェクトで新しいプロトタイプを設定し、そのオブジェクトにプロパティを追加します。  
  
```JavaScript  
var stringProp = { desc: "description" };  
  
Object.setPrototypeOf(String, stringProp);  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    Object.setPrototypeOf(s1, String); // Can't be set.  
    Object.setPrototypeOf(s2, String);  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## <a name="requirements"></a>必要条件  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]
