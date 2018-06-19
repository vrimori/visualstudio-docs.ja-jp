---
title: setUTCDate メソッド (Date) (JavaScript) |Microsoft ドキュメント
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
- setUTCDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- dates, setting
- UTC dates, setting
- setUTCDate method
ms.assetid: e6c3b876-70fe-4103-b197-6c84c078ce10
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5631a36c8b1c4f1ee50dcadb39f0f21ae5aa28e3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640602"
---
# <a name="setutcdate-method-date-javascript"></a>setUTCDate メソッド (Date) (JavaScript)
日付の月の数値を設定、`Date`オブジェクト世界協定時刻 (UTC) を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.setUTCDate(numDate)   
```  
  
## <a name="parameters"></a>パラメーター  
 `dateObj`  
 必須です。 任意の `Date` オブジェクトを指定します。  
  
 *numDate*  
 必須です。 数値を指定する月の日です。  
  
## <a name="remarks"></a>コメント  
 ローカル時刻を使用して月の日を設定するには、使用、`setDate`メソッドです。  
  
 場合の値*numDate*に格納されている月の日数の数よりも大きい、**日付**オブジェクト、または負の数値、日付が日に設定されている*numDate*負符号格納されている月の日数。 たとえば、格納されている日付は 1996 年 1 月 5 日と**setutcdate (32)** が呼び出されると、1996 年 2 月 1 日の日付変更します。 負の数値では、同様の動作があります。  
  
 **SetUTCFullYear**メソッドは、年、月、および月の日を設定するために使用できます。  
  
## <a name="example"></a>例  
 `setUTCDate` メソッドの使用例を次に示します。  
  
```JavaScript  
function SetUTCDateDemo(newdayofmonth){  
   var d = new Date();           // Create Date object.  
   d.setUTCDate(newdayofmonth);  // Set UTC day of month.  
   var s = "Current setting is ";  
   s += d.toUTCString();   
   return(s);                    // Return new setting.  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getDate メソッド (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [getUTCDate メソッド (Date)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate メソッド (Date)](../../javascript/reference/setdate-method-date-javascript.md)