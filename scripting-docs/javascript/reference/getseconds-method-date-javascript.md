---
title: "getSeconds メソッド (Date) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getSeconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- seconds method
- GetSeconds method
ms.assetid: 97b10674-af0b-4681-a846-38f972196501
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 151d720b92fb9d7068c320983a25b965078f1b2e
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="getseconds-method-date-javascript"></a>getSeconds メソッド (Date) (JavaScript)
秒数を取得、`Date`オブジェクトをローカル時刻を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.getSeconds()   
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な `dateObj` 参照は `Date` オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 0 ~ 59 の範囲の整数を返します。 時刻が現在の分に 1 秒未満の場合は、0 が返されます。 場合、`Date`時刻を指定しないでオブジェクトが作成された、既定では、秒の値は 0 です。  
  
## <a name="remarks"></a>コメント  
 世界協定時刻 (UTC) を使用して値を秒数を取得するを使用して、`getUTCSeconds`メソッドです。  
  
## <a name="example"></a>例  
 `getSeconds` メソッドを使用する方法の例を次に示します。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getSeconds());  
document.write("<br/>");  
  
date.setSeconds(5);  
document.write(date.getSeconds());  
  
// Output:  
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getUTCSeconds メソッド (Date)](../../javascript/reference/getutcseconds-method-date-javascript.md)   
 [setSeconds メソッド (Date)](../../javascript/reference/setseconds-method-date-javascript.md)   
 [setUTCSeconds メソッド (Date)](../../javascript/reference/setutcseconds-method-date-javascript.md)