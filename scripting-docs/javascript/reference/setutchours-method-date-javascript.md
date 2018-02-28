---
title: "setUTCHours メソッド (Date) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- setUTCHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- UTC times, setting
- setUTCHours method
ms.assetid: 257e36fd-fb06-4a4d-8634-d66a020a1511
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9fe83735028f86d38ef270beac6c44dfa4caae7f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="setutchours-method-date-javascript"></a>setUTCHours メソッド (Date) (JavaScript)
時間値を設定、`Date`オブジェクト世界協定時刻 (UTC) を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.setUTCHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## <a name="parameters"></a>パラメーター  
 `dateObj`  
 必須です。 任意の `Date` オブジェクトを指定します。  
  
 `numHours`  
 必須です。 時間の値に等しい数値の値です。  
  
 `numMin`  
 省略可能です。 分の値に等しい数値の値です。 いずれかを指定する必要があります`numSec`または`numMilli`使用されます。  
  
 `numSec`  
 省略可能です。 秒の値に等しい数値の値です。 場合を指定する必要があります`numMilli`引数を使用します。  
  
 `numMilli`  
 省略可能です。 ミリ秒の値に等しい数値の値です。  
  
## <a name="remarks"></a>コメント  
 すべて**設定**対応から返される値を使用する省略可能な引数を取るメソッド**取得**メソッド、省略可能な引数が指定されていない場合。 たとえば場合、`numMin`引数が指定されていない[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]から返される値を使用して、`getUTCMinutes`メソッドです。  
  
 時間値を現地時刻を設定するには、使用、`setHours`メソッドです。  
  
 引数の値の範囲を超える値や負の数をに応じて他の格納された値が変更されます。 たとえば、格納されている日付は「1996 年 1 月 5 日 00:00:00.00」と**setUTCHours(30)**が呼び出されると、日付を変更する「1996 年 1 月 6 日 06:00:00.00」。  
  
## <a name="example"></a>例  
 `setUTCHours` メソッドの使用例を次に示します。  
  
```JavaScript  
function SetUTCHoursDemo(nhr, nmin, nsec){     
   var d, s;                        // Declare variables.  
   d = new Date();                  // Create Date object.  
   d.setUTCHours(nhr, nmin, nsec);  // Set UTC hours, minutes, seconds.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                       // Return new setting.  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getHours メソッド (Date)](../../javascript/reference/gethours-method-date-javascript.md)   
 [getUTCHours メソッド (Date)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours メソッド (Date)](../../javascript/reference/sethours-method-date-javascript.md)