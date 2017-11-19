---
title: "setUTCMinutes メソッド (Date) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- dates, UTC
- UTC times, setting
- setUTCMinutes method
ms.assetid: 2415e788-6d28-46dd-a103-0931a1fd1446
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 37df1bcefa358f2c9076a3da877bd642d19178b0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="setutcminutes-method-date-javascript"></a>setUTCMinutes メソッド (Date) (JavaScript)
分の値を設定、`Date`オブジェクト世界協定時刻 (UTC) を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.setUTCMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## <a name="parameters"></a>パラメーター  
 `dateObj`  
 必須です。 任意の `Date` オブジェクトを指定します。  
  
 `numMinutes`  
 必須です。 分の値に等しい数値の値です。 次の引数のいずれかを使用する場合を指定する必要があります。  
  
 *numSeconds*  
 省略可能です。 秒の値に等しい数値の値です。 場合を指定する必要があります`numMilli`を使用します。  
  
 `numMilli`  
 省略可能です。 ミリ秒の値に等しい数値の値です。  
  
## <a name="remarks"></a>コメント  
 すべて**設定**対応から返される値を使用する省略可能な引数を取るメソッド**取得**メソッド、省略可能な引数が指定されていない場合。 たとえば場合、 *numSeconds*引数が指定されていない[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]から返される値を使用して、`getUTCSeconds`メソッドです。  
  
 分の値を現地時刻を変更するには、使用、`setMinutes`メソッドです。  
  
 引数の値の範囲を超える値や負の数をに応じて他の格納された値が変更されます。 たとえば、格納されている日付は「1996 年 1 月 5 日 00:00:00.00」と**setUTCMinutes(70)**が呼び出されると、日付を変更する「1996 年 1 月 5 日 01:10:00.00」。  
  
 **SetUTCHours**メソッドは、時間、分、秒、およびミリ秒に設定を使用することができます。  
  
## <a name="example"></a>例  
 次の例では、使用、`setUTCMinutes`メソッド。  
  
```JavaScript  
function SetUTCMinutesDemo(nmin, nsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setUTCMinutes(nmin,nsec);  // Set UTC minutes.  
   s = "Current setting is " + d.toUTCString()   
   return(s);                   // Return new setting.  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getMinutes メソッド (Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes メソッド (Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes メソッド (Date)](../../javascript/reference/setminutes-method-date-javascript.md)