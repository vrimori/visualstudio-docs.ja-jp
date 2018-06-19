---
title: getUTCMinutes メソッド (Date) (JavaScript) |Microsoft ドキュメント
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
- getUTCMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- UTC times, returning
- getUTCMinutes method
ms.assetid: b6d92543-b285-4e46-8f47-bba36e53fabd
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fe691d3b52d18340eeeff81a91c049a262277c54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
ms.locfileid: "24636812"
---
# <a name="getutcminutes-method-date-javascript"></a>getUTCMinutes メソッド (Date) (JavaScript)
(分) を取得、`Date`オブジェクト世界協定時刻 (UTC) を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.getUTCMinutes()   
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な `dateObj` 参照は `Date` オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 0 ~ 59 の範囲の整数を返します。 時間の値が 1 分未満の時間後に 0 が返されます。 場合、`Date`時刻を指定しないでオブジェクトが作成された、既定では、UTC 分の値は 0 です。 ただし、他のタイム ゾーンが異なる場合があります。  
  
## <a name="remarks"></a>コメント  
 ローカル時刻を使用して格納した分数を取得する、`getMinutes`メソッドです。  
  
## <a name="example"></a>例  
 `getUTCMinutes` メソッドの使用例を次に示します。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getUTCMinutes());  
document.write("<br/>");  
  
date.setMinutes(5);  
document.write(date.getUTCMinutes());  
  
// Output:   
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getMinutes メソッド (Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [setMinutes メソッド (Date)](../../javascript/reference/setminutes-method-date-javascript.md)   
 [setUTCMinutes メソッド (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)