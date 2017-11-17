---
title: "getUTCDate メソッド (Date) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCDate
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, UTC
- UTC dates, returning
- getUTCDate method
ms.assetid: 9e4c763f-c94c-44c9-9684-cb632d75b62e
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4c38244e989027139329ae6aab762fd9fbabb3a
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="getutcdate-method-date-javascript"></a>getUTCDate メソッド (Date) (JavaScript)
日付、世界協定時刻 (utc) を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.getUTCDate()   
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な `dateObj` 参照は `Date` オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 1 から 31、1 日の月を表す整数を返します。  
  
## <a name="remarks"></a>コメント  
 ローカル時刻を使用して月の日を取得する、`getDate`メソッドです。  
  
## <a name="example"></a>例  
 `getUTCDate` メソッドを使用する方法の例を次に示します。  
  
```JavaScript  
var date = new Date("1/23/2001");  
document.write(date.getUTCDate());  
  
// Output: 23  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getDate メソッド (Date)](../../javascript/reference/getdate-method-date-javascript.md)   
 [setDate メソッド (Date)](../../javascript/reference/setdate-method-date-javascript.md)   
 [setUTCDate メソッド (Date)](../../javascript/reference/setutcdate-method-date-javascript.md)