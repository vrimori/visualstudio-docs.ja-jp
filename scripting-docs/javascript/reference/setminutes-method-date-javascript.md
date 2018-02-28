---
title: "setMinutes メソッド (Date) (JavaScript) |Microsoft ドキュメント"
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
- setMinutes
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- minutes
- setMinutes method
ms.assetid: 34c959cd-cd29-4cee-8e04-9061cf6d42f3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ce40cb3ebf769cdd8f668e246e272833780434d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="setminutes-method-date-javascript"></a>setMinutes メソッド (Date) (JavaScript)
分の値を設定、**日付**オブジェクトのローカル時刻を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.setMinutes(numMinutes[, numSeconds[, numMilli]])   
```  
  
## <a name="parameters"></a>パラメーター  
 `dateObj`  
 必須です。 任意の `Date` オブジェクトを指定します。  
  
 `numMinutes`  
 必須です。 分の値に等しい数値の値です。 次の引数のいずれかを使用する場合を指定する必要があります。  
  
 *numSeconds*  
 省略可能です。 秒の値に等しい数値の値です。 場合を指定する必要があります、`numMilli`引数を使用します。  
  
 `numMilli`  
 省略可能です。 ミリ秒の値に等しい数値の値です。  
  
## <a name="remarks"></a>コメント  
 すべて**設定**対応から返される値を使用する省略可能な引数を取るメソッド**取得**メソッド、省略可能な引数が指定されていない場合。 たとえば場合、 *numSeconds*引数を指定しない[!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]から返される値を使用して、`getSeconds`メソッドです。  
  
 世界協定時刻 (UTC) を使用して分の値を設定するには、使用、`setUTCMinutes`メソッドです。  
  
 引数に有効範囲を超える値や負の値を指定すると、値に応じて格納される他の値が変更されます。 たとえば、格納されている日付"1996 年 1 月 5 日 00時 00分: 00"と**setMinutes(90)**が呼び出されると、日付を変更する"1996 年 1 月 5 日 1時 30分: 00 です"。 負の数値では、同様の動作があります。  
  
## <a name="example"></a>例  
 `setMinutes` メソッドの使用例を次に示します。  
  
```JavaScript  
function SetMinutesDemo(nmin, nsec){  
   var d, s;                     // Declare variables.  
   d = new Date();               // Create Date object.  
   d.setMinutes(nmin, nsec);     // Set minutes.  
   s = "Current setting is " + d.toLocaleString()   
   return(s);                    // Return new setting.  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getMinutes メソッド (Date)](../../javascript/reference/getminutes-method-date-javascript.md)   
 [getUTCMinutes メソッド (Date)](../../javascript/reference/getutcminutes-method-date-javascript.md)   
 [setUTCMinutes メソッド (Date)](../../javascript/reference/setutcminutes-method-date-javascript.md)