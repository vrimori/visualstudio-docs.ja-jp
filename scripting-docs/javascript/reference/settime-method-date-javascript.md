---
title: "setTime メソッド (Date) (JavaScript) |Microsoft ドキュメント"
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
- setTime
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- SetTime method
- time method
ms.assetid: 86584748-7219-495b-bf56-e27f5782778c
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e66b1fbf5d668330eb727e8bfc50ee9d11a28be3
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="settime-method-date-javascript"></a>setTime メソッド (Date) (JavaScript)
`Date` オブジェクトの日付と時刻の値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.setTime(milliseconds)   
```  
  
## <a name="parameters"></a>パラメーター  
 `dateObj`  
 必須です。 任意の `Date` オブジェクトを指定します。  
  
 *(ミリ秒)*  
 必須です。 GMT 1970 年 1 月 1 日の深夜から経過したミリ秒数を表す数値を指定します。  
  
## <a name="remarks"></a>コメント  
 場合*ミリ秒*は 1970 年より前に、の日付を示す、負の値。 使用可能な日付の範囲は、1970 年の約 285,616 年です。  
  
 日付と時刻を設定、`setTime`メソッドは、タイム ゾーンに依存しません。  
  
## <a name="example"></a>例  
 `setTime` メソッドの使用例を次に示します。  
  
```JavaScript  
function SetTimeTest(newtime){  
   var d, s;                  //Declare variables.  
   d = new Date();            //Create Date object.  
   d.setTime(newtime);        //Set time.  
   s = "Current setting is ";  
   s += d.toUTCString();  
   return(s);                 //Return new setting.  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getTime メソッド (Date)](../../javascript/reference/gettime-method-date-javascript.md)