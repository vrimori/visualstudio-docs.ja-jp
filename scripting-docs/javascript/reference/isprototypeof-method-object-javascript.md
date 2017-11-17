---
title: "isPrototypeOf メソッド (Object) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: isPrototypeOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: isPrototypeOf method
ms.assetid: 9c821319-c208-480f-915e-565ef6e017b6
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47ce97faecfade089bbf0b7a725a02ee73b54718
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="isprototypeof-method-object-javascript"></a>isPrototypeOf メソッド (Object) (JavaScript)
オブジェクトが別のオブジェクトのプロトタイプ チェーンに存在するかどうかを判定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
prototype.isPrototypeOf(object)  
```  
  
## <a name="parameters"></a>パラメーター  
 `prototype`  
 必須です。 オブジェクトのプロトタイプ。  
  
 `object`  
 必須です。 プロトタイプ チェーンをチェックする別のオブジェクト。  
  
## <a name="remarks"></a>コメント  
 `isPrototypeOf` のプロトタイプ チェーンに `true` がある場合、`object` メソッドは `prototype` を返します。 プロトタイプ チェインは、同じオブジェクト型のインスタンス間で機能を共有するときに使用します。 `isPrototypeOf` がオブジェクトではない場合、または `false` が `object` のプロトタイプ チェーンに存在しない場合、`prototype` メソッドは `object` を返します。  
  
## <a name="example"></a>例  
 `isPrototypeOf` メソッドの使用例を次に示します。  
  
```JavaScript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
document.write(Rectangle.prototype.isPrototypeOf(rec));  
  
// Output: true  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [prototype プロパティ (Object)](../../javascript/reference/prototype-property-object-javascript.md)