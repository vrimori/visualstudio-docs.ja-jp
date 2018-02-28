---
title: "getHours メソッド (Date) (JavaScript) |Microsoft ドキュメント"
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
- getHours
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- GetHours method
- Hours method
ms.assetid: c3936496-a213-4d15-b308-d53926ed310c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 87170f96ee6ae6b4a825436717a94749cc336ee0
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="gethours-method-date-javascript"></a>getHours メソッド (Date) (JavaScript)
ローカル時刻を使用して、日付の時間を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.getHours()   
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な `dateObj` 参照は `Date` オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 0 ~ 23 の範囲の午前 0 時からの経過時間の数を示す整数。 時刻が午前 1時 00分: 00 よりも前にある場合は、0 が返されます。 場合、`Date`時刻を指定しないでオブジェクトが作成された、既定では、時間が 0 です。  
  
## <a name="remarks"></a>コメント  
 世界協定時刻 (UTC) を使用して時間の値を取得する、`getUTCHours`メソッドです。  
  
## <a name="example"></a>例  
 `getHours` メソッドを使用する方法の例を次に示します。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getHours());  
document.write("<br/>");  
  
date.setTime(50000000);  
document.write(date.getHours());  
  
// Output:  
// 0   
// 5  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getUTCHours メソッド (Date)](../../javascript/reference/getutchours-method-date-javascript.md)   
 [setHours メソッド (Date)](../../javascript/reference/sethours-method-date-javascript.md)   
 [setUTCHours メソッド (Date)](../../javascript/reference/setutchours-method-date-javascript.md)