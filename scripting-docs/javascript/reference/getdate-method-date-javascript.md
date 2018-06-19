---
title: getDate メソッド (Date) (JavaScript) |Microsoft ドキュメント
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
- getDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, returning day of the month
- getDate method
ms.assetid: 67e7f07c-dd46-4b42-82d6-e53e4bd33703
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bfb3a8ad3ba433dc776f0831d1eac4787b8aea90
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636792"
---
# <a name="getdate-method-date-javascript"></a>getDate メソッド (Date) (JavaScript)
1 日の-月、現地時間を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.getDate()   
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な `dateObj` 参照は `Date` オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 1 ~ 31 の整数では、の日付を表します。  
  
## <a name="remarks"></a>コメント  
 1 日の-月ユニバーサル世界協定時刻 (UTC) を使用して、使用して、`getUTCDate`メソッドです。  
  
## <a name="example"></a>例  
 `getDate` メソッドの使用例を次に示します。  
  
```JavaScript  
var date = new Date("Jan 01, 2001");  
var str = "Today's date is: ";  
   str += (date.getMonth() + 1) + "/";  
   str += date.getDate() + "/";  
   str += date.getFullYear();  
document.write(str);  
  
// Output: Today's date is: 1/1/2001  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getUTCDate メソッド (Date)](../../javascript/reference/getutcdate-method-date-javascript.md)   
 [setDate メソッド (Date)](../../javascript/reference/setdate-method-date-javascript.md)   
 [setUTCDate メソッド (Date)](../../javascript/reference/setutcdate-method-date-javascript.md)