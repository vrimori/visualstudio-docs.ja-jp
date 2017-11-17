---
title: "format プロパティ (Intl.NumberFormat) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 68c3223a-023c-4fa0-aa99-d049a7a0e26a
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: be40f8e94220ad7504dd3b9736e71b3416bb3d2a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="format-property-intlnumberformat"></a>format プロパティ (Intl.NumberFormat)
指定された数値フォーマッタの設定を使用してロケール固有の数値の書式を設定する関数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
numberFormatObj.format  
```  
  
#### <a name="parameters"></a>パラメーター  
 `numberFormatObj`  
 必須です。 フォーマッタとして使用する `NumberFormat` オブジェクトの名前。  
  
## <a name="remarks"></a>コメント  
 `format` プロパティによって返される関数は、`value` という単一の引数を受け取り、`NumberFormat` オブジェクトで指定されたオプションを使用して、ローカライズされた数値を表す文字列を返します。 `value` を指定しない場合、この関数は `NaN` (非数) を返します。  
  
## <a name="example"></a>例  
 `NumberFormat` オブジェクトを使用して、ローカライズされた数値を作成する例を次に示します。  
  
```JavaScript  
var nf = new Intl.NumberFormat(["en-US"], {  
    style: "currency",  
    currency: "CNY",  
    currencyDisplay: "symbol",  
    maximumFractionDigit: 1  
})  
  
if (console && console.log) {  
    console.log(nf.format(100)); // "¥100.00"  
}  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Intl.NumberFormat オブジェクト](../../javascript/reference/intl-numberformat-object-javascript.md)