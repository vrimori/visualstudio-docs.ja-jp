---
title: Object.seal 関数 (JavaScript) |Microsoft ドキュメント
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
- Object.seal function
- seal function
ms.assetid: e72c804a-4dab-4ec9-b9df-9c9c908aa12d
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dca9066be9a557b97a52ae749cecfb218504509
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641152"
---
# <a name="objectseal-function-javascript"></a>Object.seal 関数 (JavaScript)
既存のプロパティの属性の変更、および新しいプロパティの追加を防止します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
Object.seal(object)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `object`  
 必須です。 属性をロックする対象となるオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 関数に渡されるオブジェクト。  
  
## <a name="exceptions"></a>例外  
 場合、`object`引数は、オブジェクトではない、`TypeError`例外がスローされます。  
  
## <a name="remarks"></a>コメント  
 `Object.seal`関数では、次の両方。  
  
-   により、オブジェクト以外拡張されるために新しいプロパティを追加することはできません。  
  
-   セット、`configurable`属性を`false`オブジェクトのすべてのプロパティです。  
  
 ときに、`configurable`属性は`false`プロパティの属性を変更することはできません、およびプロパティを削除することはできません。 ときに`configurable`は`false`と`writable`は`true`、`value`と`writable`属性を変更することができます。  
  
 `Object.seal`関数は変更しません、`writable`属性。  
  
 プロパティの属性を設定する方法の詳細については、次を参照してください。 [Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)です。 プロパティの属性を取得するには、使用することができます、 [Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)です。  
  
## <a name="related-functions"></a>関連する関数  
 次の関連する関数は、オブジェクトの属性の変更を禁止します。  
  
|関数|オブジェクトが拡張不能。|`configurable`設定されている`false`の各プロパティについて|`writable`設定されている`false`の各プロパティについて|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|はい|いいえ|いいえ|  
|`Object.seal`|はい|はい|いいえ|  
|[Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|はい|はい|はい|  
  
 次の関数の戻り値`true`のすべての次の表にマークされている条件に該当する場合。  
  
|関数|オブジェクトが拡張可能ですか。|`configurable``false`すべてのプロパティのですか?|`writable``false`すべてのデータ プロパティのですか?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|はい|いいえ|いいえ|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|いいえ|はい|いいえ|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|いいえ|はい|はい|  
  
## <a name="example"></a>例  
 `Object.seal` 関数の使用例を次に示します。  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
// Seal the object.  
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
 [Object.freeze 関数](../../javascript/reference/object-freeze-function-javascript.md)   
 [Object.isExtensible 関数](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed 関数](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen 関数](../../javascript/reference/object-isfrozen-function-javascript.md)