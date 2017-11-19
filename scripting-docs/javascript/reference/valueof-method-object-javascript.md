---
title: "valueOf メソッド (Object) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: valueOf
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords: valueOf method
ms.assetid: c555e38b-f451-4341-8fcd-4c8b02906a2c
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 677b56fd6fc142ce175b130d2f83291c1ac9535f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="valueof-method-object-javascript"></a>valueOf メソッド (Object) (JavaScript)
指定されたオブジェクトのプリミティブ値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object.valueOf( )  
```  
  
## <a name="remarks"></a>コメント  
 必要な`object`参照が組み込み[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]オブジェクト。  
  
 `valueOf`メソッドがごとに異なる方法で定義されている組み込み[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]オブジェクト。  
  
|オブジェクト|戻り値|  
|------------|------------------|  
|配列|配列のインスタンスを返します。|  
|ブール型|ブール値です。|  
|日付|午前 0 時、1970 年 1 月 1 日 (utc) 以降のミリ秒数で格納されている時刻の値。|  
|関数|関数自体です。|  
|数値|オブジェクトに格納されている数値を返します。|  
|オブジェクト|オブジェクト自体です。 既定値です。|  
|String|文字列値。|  
  
 **Math**と`Error`オブジェクトがない、`valueOf`メソッドです。  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
 **適用されます**:[オブジェクトの配列](../../javascript/reference/array-object-javascript.md)&#124;です。[Boolean オブジェクト](../../javascript/reference/boolean-object-javascript.md)&#124;です。[オブジェクトの日付](../../javascript/reference/date-object-javascript.md)&#124;です。[関数オブジェクト](../../javascript/reference/function-object-javascript.md)&#124;です。[オブジェクト番号](../../javascript/reference/number-object-javascript.md)&#124;です。[オブジェクトはオブジェクト](../../javascript/reference/object-object-javascript.md)&#124;です。[文字列オブジェクト](../../javascript/reference/string-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [toString メソッド (Object)](../../javascript/reference/tostring-method-object-javascript.md)