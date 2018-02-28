---
title: "setMilliseconds メソッド (Date) (JavaScript) |Microsoft ドキュメント"
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
- setMilliseconds
dev_langs:
- JavaScript
- TypeScript
- DHTML
helpviewer_keywords:
- milliseconds
- setMilliseconds method
ms.assetid: 6c398961-130e-4f60-802f-6c30e1ef4de4
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0cd339e1352511312ef9a9abf9a7ff02955c986
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/27/2017
---
# <a name="setmilliseconds-method-date-javascript"></a>setMilliseconds メソッド (Date) (JavaScript)
値を設定します (ミリ秒)、`Date`オブジェクトのローカル時刻を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
  
dateObj.  
setMilliseconds(  
numMilli  
)   
```  
  
## <a name="parameters"></a>パラメーター  
 `dateObj`  
 必須です。 任意の `Date` オブジェクトを指定します。  
  
 `numMilli`  
 必須です。 ミリ秒の値に等しい数値の値です。  
  
## <a name="remarks"></a>コメント  
 世界協定時刻 (UTC) を使用して、ミリ秒の値を設定するには、使用、`setUTCMilliseconds`メソッドです。  
  
 場合の値`numMilli`999 を超える負の数値、またはストアド秒 (と分、時間、および必要な場合など) の数がインクリメントされます、十分な量。  
  
## <a name="example"></a>例  
 `setMilliseconds` メソッドの使用例を次に示します。  
  
```JavaScript  
function SetMSecDemo(nmsec){  
   var d, s;                    // Declare variables.  
   d = new Date();              // Create Date object.  
   d.setMilliseconds(nmsec);    // Set milliseconds.  
   s = "Current setting is ";  
   s += d.toLocaleString();  
   s += " and " + d.getMilliseconds();  
   s += " milliseconds";  
   return(s);                   // Return new date setting.  
}  
```  
  
## <a name="requirements"></a>要件  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **適用対象**: [Date Object](../../javascript/reference/date-object-javascript.md)  
  
## <a name="see-also"></a>関連項目  
 [getMilliseconds メソッド (Date)](../../javascript/reference/getmilliseconds-method-date-javascript.md)   
 [getUTCMilliseconds メソッド (Date)](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)   
 [setUTCMilliseconds メソッド (Date)](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)