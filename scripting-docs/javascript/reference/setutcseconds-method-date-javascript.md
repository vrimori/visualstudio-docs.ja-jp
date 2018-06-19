---
title: setUTCSeconds メソッド (Date) (JavaScript) |Microsoft ドキュメント
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
- setUTCSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCSeconds method
- UTC times, setting
- seconds method
ms.assetid: e035e282-b39d-4d1d-8771-c17542fd6493
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3df010cd84332d8957f1c08c41c4543dec36e4a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640542"
---
# <a name="setutcseconds-method-date-javascript"></a>setUTCSeconds メソッド (Date) (JavaScript)
秒の値設定、`Date`オブジェクト世界協定時刻 (UTC) を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.setUTCSeconds(numSeconds[, numMilli])   
```  
  
## <a name="parameters"></a>パラメーター  
 `dateObj`  
 必須です。 任意の `Date` オブジェクトを指定します。  
  
 *numSeconds*  
 必須です。 秒の値に等しい数値の値です。  
  
 `numMilli`  
 省略可能です。 ミリ秒の値に等しい数値の値です。  
  
## <a name="remarks"></a>コメント  
 すべて**設定**対応から返される値を使用する省略可能な引数を取るメソッド**取得**メソッド、省略可能な引数が指定されていない場合。 たとえば場合、`numMilli`引数が指定されていない[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]から返される値を使用して、`getUTCMilliseconds`メソッドです。  
  
 秒の値を現地時刻を設定するには、使用、`setSeconds`メソッドです。  
  
 引数に有効範囲を超える値や負の値を指定すると、値に応じて格納される他の値が変更されます。 たとえば、格納されている日付は「, 1996 年 1 月 5日 00:00:00.00」と**setSeconds(150)** が呼び出されると、日付を変更する「1996 年 1 月 5 日 00:02:30.00」。  
  
 **SetUTCHours**メソッドは、時間、分、秒、およびミリ秒に設定を使用することができます。  
  
## <a name="example"></a>例  
 `setUTCSeconds` メソッドの使用例を次に示します。  
  
```JavaScript  
function SetUTCSecondsDemo(nsec){  
// Create Date object.  
    var d = new Date();       
// Set UTC seconds.  
    d.setUTCSeconds(nsec);    
    var s = "Current setting is ";  
    s += d.toUTCString();  
// Return new setting.  
    return(s);                
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getSeconds メソッド (Date)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds メソッド (Date)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds メソッド (Date)](../../javascript/reference/setseconds-method-date-javascript.md)