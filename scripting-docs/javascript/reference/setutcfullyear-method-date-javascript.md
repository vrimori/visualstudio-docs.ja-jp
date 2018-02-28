---
title: "setUTCFullYear メソッド (Date) (JavaScript) |Microsoft ドキュメント"
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
- setUTCFullYear
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- dates, UTC
- setUTCFullYear method
- UTC dates, setting
ms.assetid: e6c51b49-0149-4f9a-aa74-c73c0306f98e
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2dda8b75dd8bc8dac87ea383546f392b064c1d63
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="setutcfullyear-method-date-javascript"></a>setUTCFullYear メソッド (Date) (JavaScript)
年の値を設定、`Date`オブジェクト世界協定時刻 (UTC) を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.setUTCFullYear(numYear[, numMonth[, numDate]])   
```  
  
## <a name="parameters"></a>パラメーター  
 `dateObj`  
 必須です。 任意の `Date` オブジェクトを指定します。  
  
 `numYear`  
 必須です。 数値に相当する値の年。  
  
 `numMonth`  
 省略可能です。 数値を指定する月。 年 1 月の値は 0、およびその他の月の値が連続的に従います。 場合を指定する必要があります*numDate*を指定します。  
  
 *numDate*  
 省略可能です。 数値を指定する月の日です。  
  
## <a name="remarks"></a>コメント  
 すべて**設定**対応から返される値を使用する省略可能な引数を取るメソッド**取得**メソッド、省略可能な引数が指定されていない場合。 たとえば場合、`numMonth`引数が指定されていない[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]から返される値を使用して、`getUTCMonth`メソッドです。  
  
 また、引数の値が大きい場合をその範囲や負の値数、その他の格納された値を適宜変更されます。  
  
 ローカル時刻を使用して、年を設定するには、使用、`setFullYear`メソッドです。  
  
 サポートされている年の範囲、`Date`オブジェクトは、1970 年の約 285,616 年です。  
  
## <a name="example"></a>例  
 `setUTCFullYear` メソッドの使用例を次に示します。  
  
```JavaScript  
var dtFirst = new Date();  
dtFirst.setUTCFullYear(2007);  
  
var dtSecond = new Date();  
// 10 is the value for November.   
dtSecond.setUTCFullYear(2008, 10, 3);   
  
document.write (dtFirst.toUTCString());  
document.write ("<br />");  
document.write (dtSecond.toUTCString());  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getFullYear メソッド (Date)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [getUTCFullYear メソッド (Date)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [setFullYear メソッド (Date)](../../javascript/reference/setfullyear-method-date-javascript.md)