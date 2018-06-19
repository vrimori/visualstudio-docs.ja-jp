---
title: Object.preventExtensions 関数 (JavaScript) |Microsoft ドキュメント
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
helpviewer_keywords:
- properties [JavaScript], preventing new
- preventing new properties [JavaScript]
- preventExtensions function [JavaScript]
- Object.preventExtensions function [JavaScript]
ms.assetid: e6b48197-2374-4437-a9fe-519dd45a2077
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 868f917cc2249a1634194e4b2dd097e0dcbd4c08
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641112"
---
# <a name="objectpreventextensions-function-javascript"></a>Object.preventExtensions 関数 (JavaScript)
オブジェクトへの新しいプロパティの追加を防止します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
Object.preventExtensions(object)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `object`  
 必須です。 拡張不能にするオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 関数に渡されるオブジェクト。  
  
## <a name="exceptions"></a>例外  
 場合、`object`引数は、オブジェクトではない、`TypeError`例外がスローされます。  
  
## <a name="remarks"></a>コメント  
 `Object.preventExtensions`関数では、オブジェクト以外拡張されるために新しい名前付きプロパティを追加することはできません。 オブジェクトを拡張不能行った後にできない拡張します。  
  
 プロパティの属性を設定する方法については、次を参照してください。 [Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)です。  
  
## <a name="related-functions"></a>関連する関数  
 次の関連する関数は、オブジェクトの属性の変更を禁止します。  
  
|関数|オブジェクトが拡張不能。|`configurable`設定されている`false`の各プロパティについて|`writable`設定されている`false`の各プロパティについて|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|`Object.preventExtensions`|はい|いいえ|いいえ|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|はい|はい|いいえ|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|はい|はい|はい|  
  
 次の関数の戻り値`true`のすべての次の表にマークされている条件に該当する場合。  
  
|関数|オブジェクトが拡張可能ですか。|`configurable``false`すべてのプロパティのですか?|`writable``false`すべてのデータ プロパティのですか?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|はい|いいえ|いいえ|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|いいえ|はい|いいえ|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|いいえ|はい|はい|  
  
## <a name="example"></a>例  
 `Object.preventExtensions` 関数の使用例を次に示します。  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Make the object non-extensible.  
Object.preventExtensions(obj);  
document.write(Object.isExtensible(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.  
obj.newProp = 50;  
document.write(obj.newProp);  
  
// Output:  
// false  
// undefined  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Object.seal 関数](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze 関数](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible 関数](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed 関数](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen 関数](../../javascript/reference/object-isfrozen-function-javascript.md)