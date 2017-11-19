---
title: "setUTCMonth メソッド (Date) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setUTCMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCMonth method
- Month method
- UTC dates, setting
ms.assetid: cdac5f64-c4fd-44cc-ba3a-9a8dd3dd3fad
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 02cb69026b66e3f307a8709ab3f5b23d9518643a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="setutcmonth-method-date-javascript"></a>setUTCMonth メソッド (Date) (JavaScript)
月の値の設定、`Date`オブジェクト世界協定時刻 (UTC) を使用しています。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.setUTCMonth(numMonth[, dateVal])   
```  
  
## <a name="parameters"></a>パラメーター  
 `dateObj`  
 必須です。 任意の `Date` オブジェクトを指定します。  
  
 `numMonth`  
 必須です。 数値を指定する月。 年 1 月の値は 0、およびその他の月の値が連続的に従います。  
  
 `dateVal`  
 省略可能です。 月の日を表す数値を指定します。 指定されていない場合、値への呼び出し、`getUTCDate`メソッドを使用します。  
  
## <a name="remarks"></a>コメント  
 月の値を現地時刻を設定するには、使用、`setMonth`メソッドです。  
  
 場合の値`numMonth`11 より大きい (1 月は 0)、または負の値が格納されている年はインクリメントまたはデクリメント適切にします。 たとえば、格納されている日付は「1996 年 1 月 5 日 00:00:00.00」と**setUTCMonth(14)**が呼び出されると、日付を変更する「1997 年 3 月 5 日 00:00:00.00」。  
  
 **SetUTCFullYear**メソッドは、年、月、および月の日を設定するために使用できます。  
  
## <a name="example"></a>例  
 `setUTCMonth` メソッドの使用例を次に示します。  
  
```JavaScript  
function SetUTCMonthDemo(newmonth){  
   var d, s;                       // Declare variables.  
   d = new Date();                 // Create Date object.  
   d.setUTCMonth(newmonth);        // Set UTC month.  
   s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                      // Return new setting.  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getMonth メソッド (Date)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth メソッド (Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth メソッド (Date)](../../javascript/reference/setmonth-method-date-javascript.md)