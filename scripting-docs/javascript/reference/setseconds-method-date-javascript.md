---
title: setSeconds メソッド (Date) (JavaScript) |Microsoft ドキュメント
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
- setSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- setSeconds method
- seconds method
ms.assetid: 986ffa54-1db6-4af2-ab8b-8353f64f0b57
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b8d545307f6aac3506310c868a2860a6159a106
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24640172"
---
# <a name="setseconds-method-date-javascript"></a>setSeconds メソッド (Date) (JavaScript)
秒の値設定、`Date`オブジェクトのローカル時刻を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj  
.setSeconds(  
numSeconds[, numMilli])   
```  
  
## <a name="parameters"></a>パラメーター  
 `dateObj`  
 必須です。 任意の `Date` オブジェクトを指定します。  
  
 *numSeconds*  
 必須です。 秒の値に等しい数値の値です。  
  
 `numMilli`  
 省略可能です。 ミリ秒の値に等しい数値の値です。  
  
## <a name="remarks"></a>コメント  
 すべて**設定**対応から返される値を使用する省略可能な引数を取るメソッド**取得**メソッド、省略可能な引数が指定されていない場合。 たとえば場合、`numMilli`引数が指定されていない[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]から返される値を使用して、 **getMilliseconds**メソッドです。  
  
 値を設定する、秒の世界協定時刻 (UTC) を使用して、使用して、`setUTCSeconds`メソッドです。  
  
 引数に有効範囲を超える値や負の値を指定すると、値に応じて格納される他の値が変更されます。 たとえば、格納されている日付"1996 年 1 月 5 日 00時 00分: 00"と**setSeconds(150)** が呼び出されると、日付を変更する"1996 年 1 月 5 日 00時 02分: 30 です"。  
  
 `setHours`メソッドは、時間、分、秒、およびミリ秒に設定を使用することができます。  
  
## <a name="example"></a>例  
 `setSeconds` メソッドの使用例を次に示します。  
  
```JavaScript  
function SetSecondsDemo(nsec){  
   var d = new Date();         //Create Date object.  
   d.setSeconds(nsec);         //Set seconds.  
   var s = "Current setting is ";  
   s += d.toLocaleString();  
   return(s);                  //Return new setting.  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getSeconds メソッド (Date)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [getUTCSeconds メソッド (Date)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setUTCSeconds メソッド (Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)