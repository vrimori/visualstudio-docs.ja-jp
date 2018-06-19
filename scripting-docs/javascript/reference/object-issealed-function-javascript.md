---
title: Object.isSealed 関数 (JavaScript) |Microsoft ドキュメント
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
- properties [JavaScript], locking attributes
- isSealed function [JavaScript]
- Object.isSealed [JavaScript]
ms.assetid: af4f192e-cebe-44b9-8eef-90c096f5ae8f
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d3b9cb603a456382e3b23e6f7d0037063027b98
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24642002"
---
# <a name="objectissealed-function-javascript"></a>Object.isSealed 関数 (JavaScript)
オブジェクトの既存のプロパティ属性および値を変更できず、オブジェクトへの新しいプロパティの追加もできない場合は、`true` を返します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
Object.isSealed(object)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `object`  
 必須です。 テストするオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 `true`場合は、次の両方に該当します。  
  
-   オブジェクトは、拡張以外、オブジェクトに新しいプロパティを追加できないことを示します。  
  
-   `configurable`属性は`false`既存のすべてのプロパティです。  
  
 この関数を返しますのかどうか、オブジェクトには任意のプロパティはありません、`true`オブジェクトが拡張不能である場合。  
  
## <a name="exceptions"></a>例外  
 場合、`object`引数は、オブジェクトではない、`TypeError`例外がスローされます。  
  
## <a name="remarks"></a>コメント  
 ときに、`configurable`プロパティの属性が`false`プロパティの属性を変更することはできません、およびプロパティを削除することはできません。 ときに`writable`は`false`、データ プロパティの値を変更することはできません。 ときに`configurable`は`false`と`writable`は`true`、`value`と`writable`属性を変更することができます。  
  
 `Object.isSealed`関数が使用しない、`writable`プロパティを確認して、戻り値の属性です。  
  
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
|`Object.isSealed`|いいえ|はい|いいえ|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|いいえ|はい|はい|  
  
## <a name="example"></a>例  
 `Object.isSealed` 関数の使用例を次に示します。  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Seal the object, and verify that it is sealed.  
Object.seal(obj);  
document.write(Object.isSealed(obj));  
document.write("<br/>");  
  
// Try to add a new property, and then verify that it is not added.   
obj.newProp = 50;  
document.write(obj.newProp);  
document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
  
// Output:  
// true  
// undefined  
// 10  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Object.preventExtensions 関数](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal 関数](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.freeze 関数](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible 関数](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isFrozen 関数](../../javascript/reference/object-isfrozen-function-javascript.md)   
 [Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)   
 [Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)