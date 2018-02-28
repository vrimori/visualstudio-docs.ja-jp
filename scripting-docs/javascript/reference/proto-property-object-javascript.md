---
title: "_ _proto _ _ プロパティ (Object) (JavaScript) |Microsoft ドキュメント"
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
- __proto__
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 97c3f84d-125e-4905-b921-b021264964ee
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e38669c400acba6f4ed3c4ee3fb5836c31b1bc00
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="proto-property-object-javascript"></a>__proto__プロパティ (Object) (JavaScript)
指定されたオブジェクトの内部プロトタイプへの参照が含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
object.__proto__  
```  
  
#### <a name="parameters"></a>パラメーター  
 `object`  
 必須です。 プロトタイプの設定対象となるオブジェクト。  
  
## <a name="remarks"></a>コメント  
 `__proto__` プロパティを使用して、オブジェクトのプロトタイプを設定できます。  
  
 オブジェクトまたは関数は、新しいプロトタイプのすべてのメソッドとプロパティに加えて、新しいプロトタイプのプロトタイプ チェーン内のすべてのメソッドとプロパティを継承します。 オブジェクトが保持できるプロトタイプは 1 つだけであるため (プロトタイプ チェーン内の継承されたプロトタイプは含まれない)、`__proto__` プロパティを呼び出すと、前のプロトタイプが置き換えられます。  
  
 プロトタイプは拡張可能オブジェクトでのみ設定できます。 詳細については、次を参照してください。 [Object.preventExtensions 関数](../../javascript/reference/object-preventextensions-function-javascript.md)です。  
  
> [!NOTE]
>  `__proto__` プロパティ名の先頭と末尾には 2 つのアンダースコアが付いています。  
  
## <a name="example"></a>例  
 オブジェクトのプロトタイプを設定する方法のコード例を次に示します。  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns true  
    rec.__proto__ = Object.prototype;  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns false  
}  
```  
  
## <a name="example"></a>例  
 次のコード例は、プロパティをプロトタイプに追加することによってオブジェクトに追加する方法を示しています。  
  
```JavaScript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
obj.__proto__ = proto;  
  
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
  
String.__proto__ = stringProp;  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    s1.__proto__ = String;  // Can't be set.  
    s2.__proto__ = String;  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [プロトタイプおよびプロトタイプの継承](../../javascript/advanced/prototypes-and-prototype-inheritance.md)