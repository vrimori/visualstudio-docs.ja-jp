---
title: "setHours メソッド (Date) (JavaScript) |Microsoft ドキュメント"
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
- setHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- hours
- setHours method
- dates, setting
ms.assetid: 460f742d-f8d2-4874-9d07-2fb969fef066
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f9757f8416953eaf756dba96b91100527606cf9c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="sethours-method-date-javascript"></a>setHours メソッド (Date) (JavaScript)
時間の値を設定、`Date`オブジェクトのローカル時刻を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.setHours(numHours[, numMin[, numSec[, numMilli]]])   
```  
  
## <a name="parameters"></a>パラメーター  
 `dateObj`  
 必須です。 任意の `Date` オブジェクトを指定します。  
  
 `numHours`  
 必須です。 時間の値に等しい数値の値です。  
  
 `numMin`  
 省略可能です。 分の値に等しい数値の値です。 次の引数のいずれかを使用する場合を指定する必要があります。  
  
 `numSec`  
 省略可能です。 秒の値に等しい数値の値です。 次の引数を使用する場合を指定する必要があります。  
  
 `numMilli`  
 省略可能です。 ミリ秒の値に等しい数値の値です。  
  
## <a name="remarks"></a>コメント  
 すべて**設定**対応から返される値を使用する省略可能な引数を取るメソッド**取得**メソッド、省略可能な引数が指定されていない場合。 たとえば場合、`numMinutes`引数が指定されていない[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]から返される値を使用して、`getMinutes`メソッドです。  
  
 世界協定時刻 (UTC) を使用して時間の値を設定するには、使用、`setUTCHours`メソッドです。  
  
 引数に有効範囲を超える値や負の値を指定すると、値に応じて格納される他の値が変更されます。 たとえば、格納されている日付"1996 年 1 月 5 日 00時 00分: 00"、および**setHours(30)**が呼び出されると、日付を変更する"1996 年 1 月 6 日 06時 00分: 00 です"。 負の数値では、同様の動作があります。  
  
## <a name="example"></a>例  
 `setHours` メソッドの使用例を次に示します。  
  
```JavaScript  
function SetHoursDemo(nhr, nmin, nsec){  
   var d, s;                     //Declare variables.  
   d = new Date();               //Create Date object.  
   d.setHours(nhr, nmin, nsec);  //Set hours, minutes, & seconds.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    //Return new date setting.  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getHours メソッド (Date)](../../javascript/reference/gethours-method-date-javascript.md)   
 [getUTCHours メソッド (Date)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setUTCHours メソッド (Date)](../../javascript/reference/setutchours-method-date-javascript.md)