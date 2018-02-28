---
title: "getMilliseconds メソッド (Date) (JavaScript) |Microsoft ドキュメント"
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
- getMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- getMilliseconds method
ms.assetid: 1b512146-1e8a-44a4-89da-6cc5338d15cb
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33e5fc54dffbe06e47f0978e6cef94b1f650c90f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="getmilliseconds-method-date-javascript"></a>getMilliseconds メソッド (Date) (JavaScript)
ローカル時刻を使用して、日付のミリ秒数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.getMilliseconds()   
```  
  
#### <a name="parameters"></a>パラメーター  
 必要な `dateObj` 参照は `Date` オブジェクトです。  
  
## <a name="return-value"></a>戻り値  
 日付のミリ秒単位で返します。 値の範囲は 0 ~ 999 です。 場合は、ミリ秒を指定することがなく、日付を構築すると、返される値は 0 です。  
  
## <a name="remarks"></a>コメント  
 世界協定時刻 (UTC) でミリ秒単位の数を取得する、`getUTCMilliseconds`メソッドです。  
  
## <a name="example"></a>例  
 次の例を使用する方法を示しています、 **getMilliseconds**メソッドです。  
  
```JavaScript  
var date = new Date("1/1/2001");  
document.write(date.getMilliseconds());  
document.write("<br/>");  
  
date.setMilliseconds(5);  
document.write(date.getMilliseconds());  
// Output:   
// 0  
// 5  
  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getUTCMilliseconds メソッド (Date)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setMilliseconds メソッド (Date)](../../javascript/reference/setmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds メソッド (Date)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)