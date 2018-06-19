---
title: Object.isFrozen 関数 (JavaScript) |Microsoft ドキュメント
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
- isFrozen function [JavaScript]
- Object.isFrozen function [JavaScript]
ms.assetid: 6cf1bbc6-56e8-429b-8e2c-0024fa614acc
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3e1ccd11d5b4ef3b5f24dbfc8e815f0e3e156347
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641712"
---
# <a name="objectisfrozen-function-javascript"></a>Object.isFrozen 関数 (JavaScript)
返します`true`かどうか、オブジェクトで既存のプロパティ属性と値は変更できませんし、オブジェクトに新しいプロパティを追加することはできません。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
Object.isFrozen(object)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `object`  
 必須です。 テストするオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 `true`場合は、次のすべてに該当します。  
  
-   オブジェクトは、拡張以外、オブジェクトに新しいプロパティを追加できないことを示します。  
  
-   `configurable`属性は`false`既存のすべてのプロパティです。  
  
-   `writable`属性は`false`既存のすべてのデータ プロパティです。  
  
 この関数を返しますのかどうか、オブジェクトは既存のプロパティを持たない、`true`オブジェクトが拡張以外の場合。  
  
## <a name="exceptions"></a>例外  
 場合、`object`引数は、オブジェクトではない、`TypeError`例外がスローされます。  
  
## <a name="remarks"></a>コメント  
 ときに、`configurable`プロパティの属性が`false`プロパティの属性を変更することはできません、およびプロパティを削除することはできません。 ときに`writable`は`false`、データ プロパティの値を変更することはできません。 ときに`configurable`は`false`と`writable`は`true`、`value`と`writable`属性を変更することができます。  
  
 プロパティの属性を設定する方法については、次を参照してください。 [Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)です。 プロパティの属性を取得するには、使用することができます、 [Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)です。  
  
## <a name="related-functions"></a>関連する関数  
 次の関連する関数は、オブジェクトの属性の変更を禁止します。  
  
|関数|オブジェクトが拡張不能。|`configurable`設定されている`false`の各プロパティについて|`writable`設定されている`false`の各プロパティについて|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|はい|いいえ|いいえ|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|はい|はい|いいえ|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|はい|はい|はい|  
  
 次の関数の戻り値`true`のすべての次の表にマークされている条件に該当する場合。  
  
|関数|オブジェクトが拡張可能ですか。|`configurable``false`すべてのプロパティのですか?|`writable``false`すべてのデータ プロパティのですか?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|はい|いいえ|いいえ|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|いいえ|はい|いいえ|  
|`Object.isFrozen`|いいえ|はい|はい|  
  
## <a name="example"></a>例  
 `Object.isFrozen` 関数の使用例を次に示します。  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object, and verify that it is frozen.  
Object.freeze(obj);  
document.write(obj.isFrozen());  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write (obj.newProp);  
document.write ("<br/>");  
  
// Try to delete a property, and then verify that it is still present.  
delete obj.length;  
document.write (obj.length);  
document.write ("<br/> ");  
  
// Try to change a property value, and then verify that it is not changed.  
obj.pasta = "linguini";  
document.write (obj.pasta);  
  
// Output:  
// true  
// undefined  
// 10  
// spaghetti  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Object.preventExtensions 関数](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal 関数](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze 関数](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible 関数](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed 関数](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)   
 [Object.getOwnPropertyNames 関数](../../javascript/reference/object-getownpropertynames-function-javascript.md)