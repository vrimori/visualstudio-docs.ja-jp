---
title: hasOwnProperty メソッド (Object) (JavaScript) |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- hasOwnProperty
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hasOwnProperty method
ms.assetid: 3eb69d69-486f-4792-9518-4452aef369ca
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 397b68fc87bf730886c928e099037ff0183a7f63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24637302"
---
# <a name="hasownproperty-method-object-javascript"></a>hasOwnProperty メソッド (Object) (JavaScript)
指定された名前のプロパティがオブジェクトにあるかどうかを確認します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.hasOwnProperty(proName)  
```  
  
## <a name="parameters"></a>パラメーター  
 `object`  
 必須です。 オブジェクトのインスタンスを指定します。  
  
 `proName`  
 必須です。 プロパティ名の文字列値を指定します。  
  
## <a name="remarks"></a>コメント  
 指定した名前のプロパティが `hasOwnProperty` にある場合、`true` メソッドは `object` を返し、プロパティがない場合は `false` を返します。 このメソッドは、オブジェクトのプロトタイプ チェインにあるプロパティをチェックしません。プロパティはオブジェクト自身のメンバーである必要があります。  
  
 このプロパティは、Internet Explorer 8 およびそれ以前のホスト オブジェクトではサポートされません。  
  
## <a name="example"></a>例  
 すべての `String` オブジェクトが共通メソッド split を共有している場合の例を次に示します。 次のコードが表示されます**false**と**true**です。  
  
```JavaScript  
var s = new String("Sample");  
document.write(s.hasOwnProperty("split"));  
document.write("<br/>");  
document.write(String.prototype.hasOwnProperty("split"));  
  
// Output:  
// false  
// true  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [in 演算子](../../javascript/reference/in-operator-decrementjavascript.md)