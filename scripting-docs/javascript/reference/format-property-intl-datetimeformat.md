---
title: "format プロパティ (Intl.DateTimeFormat) |Microsoft ドキュメント"
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
ms.assetid: 487930fe-a948-446f-902d-06bb0d7685d5
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e94fcd797a63944d0162dceadf773cf9b15f943
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="format-property-intldatetimeformat"></a>format プロパティ (Intl.DateTimeFormat)
指定された日時フォーマッタの設定を使用してロケール固有の日付の書式を設定する関数を返します。  
  
## <a name="syntax"></a>構文  
  
```  
dateTimeFormatObj.format  
```  
  
#### <a name="parameters"></a>パラメーター  
 `dateTimeFormatObj`  
 必須です。 フォーマッタとして使用する `DateTimeFormat` オブジェクトの名前。  
  
## <a name="remarks"></a>コメント  
 `format` プロパティによって返される関数は、`date` という単一の引数を受け取り、`DateTimeFormat` オブジェクトで指定されたオプションを使用して、ローカライズされた日付を表す文字列を返します。 返される関数の `date` パラメーターは、数値、日付文字列、または `Date` オブジェクトである必要があります。 場合`date`が提供されていない場合、関数を使用して[Date.now](../../javascript/reference/date-now-function-javascript.md)として既定の入力値。  
  
## <a name="example"></a>例  
 次の例では、`DateTimeFormat` オブジェクトを使用して、日付 "Dec 1, 2007" をドイツ語にローカライズし、書式を再設定します。  
  
```JavaScript  
var dtFormat = new Intl.DateTimeFormat(["de"], {  
    year: "numeric",  
    month: "long",  
    day: "2-digit",  
    hour: "numeric"  
});  
  
if (console && console.log) {  
    console.log(dtFormat.format(new Date("Dec 1, 2007")));  
    // Returns 01. Dezember 2007 00:00  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [Intl.DateTimeFormat オブジェクト](../../javascript/reference/intl-datetimeformat-object-javascript.md)