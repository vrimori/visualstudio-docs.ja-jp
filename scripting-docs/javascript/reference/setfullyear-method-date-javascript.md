---
title: "setFullYear メソッド (Date) (JavaScript) |Microsoft ドキュメント"
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
- setFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Year method
- setFullYear method
- dates, setting
ms.assetid: 635e4f5a-0210-4c01-8152-b0da4146f6ff
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e5e20a8486d1aefeab9b244c5f1e9d1b1e60c3f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="setfullyear-method-date-javascript"></a>setFullYear メソッド (Date) (JavaScript)
年を設定します、`Date`オブジェクトのローカル時刻を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.setFullYear(numYear[, numMonth[, numDate]])   
```  
  
## <a name="parameters"></a>パラメーター  
 `dateObj`  
 必須です。 任意の `Date` オブジェクトを指定します。  
  
 `numYear`  
 必須です。 年の数値。  
  
 `numMonth`  
 省略可能です。 0 から始まる数値の月 (1、月 11 日 12 月の場合は 0)。 場合に指定する必要があります`numDate`を指定します。  
  
 `numDate`  
 省略可能です。 数値の月の日と同じです。  
  
## <a name="remarks"></a>コメント  
 すべて**設定**対応から返される値を使用する省略可能な引数を取るメソッド**取得**メソッド、省略可能な引数が指定されていない場合。 たとえば場合、`numMonth`引数は省略可能だが指定されていない[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]から返される値を使用して、 **getMonth**メソッドです。  
  
 さらに、引数の値の予定表の範囲を超える値や負の値を日付は前方または後方に適切なをロールアップします。  
  
 世界協定時刻 (UTC) を使用して、年を設定するには、使用、`setUTCFullYear`メソッドです。  
  
 Date オブジェクトでサポートされている年の範囲は、1970年の前後の約 285,616 年です。  
  
## <a name="example"></a>例  
 次の例では、使用、`setFullYear`メソッド。  
  
```JavaScript  
var date1 = new Date("1/1/2001");  
date1.setFullYear(2007);  
  
var date2 = new Date("1/1/2001");  
date2.setFullYear(2008, 10, 3);   
  
document.write (date1.toLocaleString());  
document.write ("<br />");  
document.write (date2.toLocaleString());  
  
// Output:  
// Monday, January 01, 2007 12:00:00 AM  
// Monday, November 03, 2008 12:00:00 AM  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getFullYear メソッド (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear メソッド (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setUTCFullYear メソッド (Date)](../../javascript/reference/setutcfullyear-method-date-javascript.md)