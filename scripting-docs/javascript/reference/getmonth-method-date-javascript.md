---
title: "getMonth メソッド (Date) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getMonth
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- Date object
- dates, month value
- Month method
- GetMonth method
ms.assetid: c20dd8ba-1d78-42f1-8717-ed3dfd2362dd
caps.latest.revision: "14"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eeffd7ffc7bee5fa63607e342a9a9dced7088d35
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="getmonth-method-date-javascript"></a>getMonth メソッド (Date) (JavaScript)
ローカル時刻を使用して、月を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.getMonth()   
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な `dateObj` 参照は `Date` オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 `getMonth`メソッドは、0 (1 月) および 11 (12 月) の整数を返します。 `Date` 「1996 年 1 月 5日」で構築された`getMonth`0 を返します。  
  
## <a name="remarks"></a>コメント  
 世界協定時刻 (UTC) を使用して月の値を取得する、`getUTCMonth`メソッドです。  
  
## <a name="example"></a>例  
 `getMonth` メソッドを使用する方法の例を次に示します。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMonth());  
  
// Output: 0  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getUTCMonth メソッド (Date)](../../javascript/reference/getutcmonth-method-date-javascript.md)   
 [setMonth メソッド (Date)](../../javascript/reference/setmonth-method-date-javascript.md)   
 [setUTCMonth メソッド (Date)](../../javascript/reference/setutcmonth-method-date-javascript.md)