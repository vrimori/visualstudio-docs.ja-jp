---
title: "setDate メソッド (Date) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: setDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- setDate method
- dates, setting
ms.assetid: a84b9b01-a6d0-489f-8a13-e7af9e9630b2
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8d74340287b3a7348419d302f79775eb610c6983
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="setdate-method-date-javascript"></a>setDate メソッド (Date) (JavaScript)
日付の数値を設定、`Date`オブジェクトのローカル時刻を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.setDate(numDate)   
```  
  
## <a name="parameters"></a>パラメーター  
 `dateObj`  
 必須です。 任意の `Date` オブジェクトを指定します。  
  
 `numDate`  
 必須です。 数値を指定する月の日です。  
  
## <a name="remarks"></a>コメント  
 世界協定時刻 (UTC) を使用して日付の値を設定するには、使用、`setUTCDate`メソッドです。  
  
 場合の値`numDate`月の日数を以降の月または年を日付ロールバックの数よりも大きいです。 たとえば、格納されている日付は 1996 年 1 月 5 日と`setDate(32)`が呼び出されると、1996 年 2 月 1 日の日付変更します。 場合`numDate`負の数値、以前の月または年に日付ロールバックします。 たとえば、格納されている日付は 1996 年 1 月 5 日と`setDate(-32)`が呼び出されると、1995 年 11 月 29 日の日付変更します。  
  
 [SetFullYear メソッド (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)年、月、および月の日を設定するために使用できます。  
  
## <a name="example"></a>例  
 `setDate` メソッドを使用する方法の例を次に示します。  
  
```JavaScript  
var date = new Date("12/15/1990");  
date.setDate(30);  
document.write(date);  
  
// Output (for the PST time zone): Sun Dec 30 00:00:00 PST 1990  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getDate メソッド (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [setFullYear メソッド (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [setMonth メソッド (Date)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCDate メソッド (Date)](../../javascript/reference/setutcdate-method-date-javascript.md)