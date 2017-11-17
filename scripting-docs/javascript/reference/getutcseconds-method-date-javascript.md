---
title: "getUTCSeconds メソッド (Date) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getUTCSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- UTC times, returning
- seconds method
- getUTCSeconds method
ms.assetid: 2d8ea7dc-79f8-4a9b-b2ab-732db2bcd5fd
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4f398145f8e31ed633bf3215de7d5a5ef669b7ef
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="getutcseconds-method-date-javascript"></a>getUTCSeconds メソッド (Date) (JavaScript)
秒数を取得、`Date`オブジェクト世界協定時刻 (UTC) を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.getUTCSeconds()   
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な `dateObj` 参照は `Date` オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 0 ~ 59 の範囲の整数を返します。 時刻が現在の分に 1 秒未満の場合は、0 が返されます。 場合、`Date`時刻を指定しないでオブジェクトが作成された、既定では、UTC (秒) 値は 0 です。  
  
## <a name="remarks"></a>コメント  
 ローカル時刻の秒数を取得する、`getSeconds`メソッドです。  
  
## <a name="example"></a>例  
 `getUTCSeconds` メソッドを使用する方法の例を次に示します。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date. getUTCSeconds());  
  
// Output: 0  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getSeconds メソッド (Date)](../../javascript/reference/getseconds-method-date-javascript.md)   
 [setSeconds メソッド (Date)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds メソッド (Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)