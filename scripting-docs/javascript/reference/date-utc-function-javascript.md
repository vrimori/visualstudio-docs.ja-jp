---
title: "Date.UTC 関数 (JavaScript) |Microsoft ドキュメント"
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
- UTC
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC function [JavaScript]
- UTC dates, returning
- Date.UTC function [JavaScript]
ms.assetid: c0d67ce1-a47e-4dfd-bbf4-21619c406a0f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a6a7c5622b74699e3d718ceb65e96638bdb6c3c5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="dateutc-function-javascript"></a>Date.UTC 関数 (JavaScript)
午前 0 時、1970 年 1 月 1 日までのミリ秒数を返します世界協定時刻 (UTC) (つまり GMT) と、指定した日付。  
  
## <a name="syntax"></a>構文  
  
```  
Date.UTC(year, month, day[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## <a name="parameters"></a>パラメーター  
 `year`  
 必須です。 完全な年表記は、クロス世紀日付の精度に必要です。 場合`year`0 ~ 99 の範囲が使用されており、 `year` 1900 と見なされます +`year`です。  
  
 `month`  
 必須です。 月を表す 0 ～ 11 (1 ～ 12 月に相当) の範囲内の整数を指定します。  
  
 `day`  
 必須です。 日を表す 1 ～ 31 の範囲内の整数を指定します。  
  
 `hours`  
 省略可能です。 引数 `minutes` を指定する場合は、この引数を指定する必要があります。 時を表す 0 ～ 23 (午前 0 時 ～ 午後 11 時に対応) の範囲内の整数を指定します。  
  
 `minutes`  
 省略可能です。 引数 `seconds` を指定する場合は、この引数を指定する必要があります。 分を表す 0 ～ 59 の範囲内の整数を指定します。  
  
 `seconds`  
 省略可能です。 引数 `milliseconds` を指定する場合は、この引数を指定する必要があります。 秒を表す 0 ～ 59 の範囲内の整数を指定します。  
  
 `ms`  
 省略可能です。 ミリ秒を表す 0 ～ 999 の範囲内の整数を指定します。  
  
## <a name="remarks"></a>コメント  
 `Date.UTC`関数は、午前 0 時、1970 年 1 月 1 日 UTC と、指定した日付までのミリ秒数を返します。 この戻り値で使用することができます、`setTime`メソッドと、`Date`オブジェクト コンス トラクターです。 引数の値の範囲を超える値や負の数をに応じて他の格納された値が変更されます。 たとえば、150 秒を指定すると、[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] で 2 分 30 秒として処理されます。  
  
 間の違い、`Date.UTC`関数および`Date`する日付を受け入れるオブジェクト コンス トラクターは、`Date.UTC`関数には、UTC が前提としています、`Date`オブジェクト コンス トラクターには、ローカル時間が前提としています。  
  
## <a name="example"></a>例  
 `Date.UTC` 関数の使用例を次に示します。  
  
```JavaScript  
// Determine the milliseconds per day.  
 var MinMilli = 1000 * 60;  
var HrMilli = MinMilli * 60;  
var DyMilli = HrMilli * 24;  
  
var date = new Date("June 1, 1990");  
var year = date.getFullYear();  
var month = date.getMonth();  
var day = date.getDay();  
  
var newDay = new Date("January 16, 2020");  
var yeartoday = newDay.getUTCFullYear();  
var monthtoday = newDay.getUTCMonth();  
var dayofmonthtoday = newDay.getUTCDate();  
  
// Get the milliseconds since 1/1/1970 UTC.  
var t1 = Date.UTC(year, month - 1, day)  
var t2 = Date.UTC(yeartoday, monthtoday, dayofmonthtoday);  
  
// Determine the difference in days.  
var days = (t2 - t1) / DyMilli;  
  
document.write(days);  
// Output: 10848  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [setTime メソッド (Date)](../../javascript/reference/settime-method-date-javascript.md)