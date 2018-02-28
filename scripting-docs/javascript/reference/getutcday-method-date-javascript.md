---
title: "getUTCDay メソッド (Date) (JavaScript) |Microsoft ドキュメント"
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
- getUTCDay
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, UTC
- UTC dates, returning
- getUTCDay method
ms.assetid: 2fceb5b0-6f77-4919-82c3-0877fd55bacb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6ee9953a7abf548ef15cc124e09b914af360ca23
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="getutcday-method-date-javascript"></a>getUTCDay メソッド (Date) (JavaScript)
世界協定時刻 (UTC) を使用して曜日を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.getUTCDay()   
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な `dateObj` 参照は `Date` オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 0 (日曜日) ~ 6 (土曜日) を週の曜日を表す範囲の整数を返します。  
  
## <a name="remarks"></a>コメント  
 ローカル時刻を使用して曜日を取得する、`getDate`メソッドです。  
  
## <a name="example"></a>例  
 `getUTCDay` メソッドを使用する方法の例を次に示します。  
  
```JavaScript  
var date = new Date("2/6/2001");  
var day = date.getUTCDay();  
document.write(day);  
  
// Output: 2  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getDay メソッド (Date)](../../javascript/reference/getday-method-date-javascript.md)