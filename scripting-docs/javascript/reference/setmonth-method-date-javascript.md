---
title: "setMonth メソッド (Date) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Month method
- setMonth method
ms.assetid: 4f5be295-d536-46c0-b3a4-ad06457efe82
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f2672abebd327af8b0da58d46ebc183b8159711
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="setmonth-method-date-javascript"></a>setMonth メソッド (Date) (JavaScript)
月の値の設定、`Date`オブジェクトのローカル時刻を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj. setMonth(numMonth[, dateVal])   
```  
  
## <a name="parameters"></a>パラメーター  
 `dateObj`  
 必須です。 任意の `Date` オブジェクトを指定します。  
  
 `numMonth`  
 必須です。 数値を指定する月。 年 1 月の値は 0、およびその他の月の値が連続的に従います。  
  
 `dateVal`  
 省略可能です。 月の日を表す数値を指定します。 この値が指定されていない場合、値への呼び出し、`getDate`メソッドを使用します。  
  
## <a name="remarks"></a>コメント  
 世界協定時刻 (UTC) を使用して月の値を設定するには、使用、`setUTCMonth`メソッドです。  
  
 場合の値`numMonth`11 より大きい (1 月は 0) または負の値が格納されている年が変更されます。 たとえば、格納されている日付は、「Jan 5, 1996"と**setMonth(14)**が呼び出されると、日付が"1997 年 3 月 5 日です"に変更されます  
  
 **SetFullYear**メソッドは、年、月、および月の日を設定するために使用できます。  
  
## <a name="example"></a>例  
 `setMonth` メソッドの使用例を次に示します。  
  
```JavaScript  
date = new Date('1/1/1990');  
date.setMonth(14);  
document.write(date);  
  
// Output: Fri Mar 1 00:00:00 PST 1991  
// Note that the time zone corresponds to the time zone on the local computer.  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getMonth メソッド (Date)](../../javascript/reference/getmonth-method-date-javascript.md)   
 [getUTCMonth メソッド (Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setUTCMonth メソッド (Date)](../../javascript/reference/setutcmonth-method-date-javascript.md)