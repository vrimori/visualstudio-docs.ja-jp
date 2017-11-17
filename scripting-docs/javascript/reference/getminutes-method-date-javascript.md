---
title: "getMinutes メソッド (Date) (JavaScript) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.technology: devlang-javascript
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: getMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- GetMinutes method
- minutes method
ms.assetid: d4139b5d-04e1-474c-9a83-e9d40597243a
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff08fd84345c9ceb816444a1b44643a8353b60b1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="getminutes-method-date-javascript"></a>getMinutes メソッド (Date) (JavaScript)
(分) を取得、`Date`オブジェクトをローカル時刻を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.getMinutes()   
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な `dateObj` 参照は `Date` オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 0 ~ 59 の範囲の整数を返します。 時間の値が 1 分未満の時間後に 0 が返されます。 場合、`Date`時刻を指定しないでオブジェクトが作成された、既定では分の値は 0 です。  
  
## <a name="remarks"></a>コメント  
 世界協定時刻 (UTC) を使用して分の値を取得する、`getUTCMinutes`メソッドです。  
  
## <a name="example"></a>例  
 例を次にする方法、`getMinutes`メソッドです。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getMinutes());  
  
// Output:  
// 0  
// 5  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getUTCMinutes メソッド (Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setMinutes メソッド (Date)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes メソッド (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)