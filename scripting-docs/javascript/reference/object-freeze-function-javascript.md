---
title: Object.freeze 関数 (JavaScript) |Microsoft ドキュメント
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
- Object.freeze function
- freeze function
ms.assetid: 83ffe193-0a37-4e0c-9b66-44c422765fb3
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec08b34c3c8b32245928e6e75f5df1fbdfe2d4a6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24641822"
---
# <a name="objectfreeze-function-javascript"></a>Object.freeze 関数 (JavaScript)
既存のプロパティ属性と値の変更、および新しいプロパティの追加を防止します。  
  
## <a name="syntax"></a>構文  
  
```JavaScript  
Object.freeze(object)  
```  
  
#### <a name="parameters"></a>パラメーター  
 `object`  
 必須です。 属性をロックする対象となるオブジェクト。  
  
## <a name="return-value"></a>戻り値  
 関数に渡されるオブジェクト。  
  
## <a name="exceptions"></a>例外  
 場合、`object`引数は、オブジェクトではない、`TypeError`例外がスローされます。  
  
## <a name="remarks"></a>コメント  
 `Object.freeze`関数は、次を実行します。  
  
-   により、オブジェクト以外拡張されるために新しいプロパティを追加することはできません。  
  
-   セット、`configurable`属性を`false`オブジェクトのすべてのプロパティです。 ときに`configurable`は`false`プロパティの属性を変更することはできません、およびプロパティを削除することはできません。  
  
-   セット、`writable`属性を`false`オブジェクトのすべてのデータ プロパティです。 ときに`writable`が false の場合、データのプロパティ値を変更することはできません。  
  
 プロパティの属性を設定する方法の詳細については、次を参照してください。 [Object.defineProperty 関数](../../javascript/reference/object-defineproperty-function-javascript.md)です。 プロパティの属性を取得するには、使用することができます、 [Object.getOwnPropertyDescriptor 関数](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)です。  
  
## <a name="related-functions"></a>関連する関数  
 次の関連する関数は、オブジェクトの属性の変更を禁止します。  
  
|関数|オブジェクトが拡張不能。|`configurable`設定されている`false`の各プロパティについて|`writable`設定されている`false`の各プロパティについて|  
|--------------|------------------------------------|--------------------------------------------------------|----------------------------------------------------|  
|[Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|はい|いいえ|いいえ|  
|[Object.seal](../../javascript/reference/object-seal-function-javascript.md)|はい|はい|いいえ|  
|`Object.freeze`|はい|はい|はい|  
  
 次の関数の戻り値`true`のすべての次の表にマークされている条件に該当する場合。  
  
|関数|オブジェクトが拡張可能ですか。|`configurable``false`すべてのプロパティのですか?|`writable``false`すべてのデータ プロパティのですか?|  
|--------------|---------------------------|---------------------------------------------------|----------------------------------------------------|  
|[Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|はい|いいえ|いいえ|  
|[Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|いいえ|はい|はい|  
|[Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|いいえ|はい|はい|  
  
## <a name="example"></a>例  
 `Object.freeze` 関数の使用例を次に示します。  
  
```JavaScript  
// Create an object that has two properties.  
var obj = { pasta: "spaghetti", length: 10 };  
  
// Freeze the object.  
Object.freeze(obj);  
  
// Try to add a new property, and then verify that it is not added.   
    obj.newProp = 50;  
    document.write(obj.newProp);  
    document.write("<br/>");  
  
// Try to delete a property, and then verify that it is still present.   
delete obj.length;  
document.write(obj.length);  
document.write("<br/>");  
  
// Try to change a property value, and then verify that it is not changed.   
obj.pasta = "linguini";  
document.write(obj.pasta);  
  
// Output:  
// undefined  
// 10  
// spaghetti  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv9](../../javascript/includes/jsv9-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Object.preventExtensions 関数](../../javascript/reference/object-preventextensions-function-javascript.md)   
 [Object.seal 関数](../../javascript/reference/object-seal-function-javascript.md)   
 [Object.isExtensible 関数](../../javascript/reference/object-isextensible-function-javascript.md)   
 [Object.isSealed 関数](../../javascript/reference/object-issealed-function-javascript.md)   
 [Object.isFrozen 関数](../../javascript/reference/object-isfrozen-function-javascript.md)